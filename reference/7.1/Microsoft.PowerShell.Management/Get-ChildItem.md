---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: c29a938fc73b8b69ea1bbf96f12f5d42d16f79bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251348"
---
# <span data-ttu-id="e13b1-103">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="e13b1-103">Get-ChildItem</span></span>

## <span data-ttu-id="e13b1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e13b1-104">SYNOPSIS</span></span>

<span data-ttu-id="e13b1-105">Hiermee worden de items en onderliggende items in een of meer opgegeven locaties opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-105">Gets the items and child items in one or more specified locations.</span></span>

## <span data-ttu-id="e13b1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e13b1-106">SYNTAX</span></span>

### <span data-ttu-id="e13b1-107">Items (standaard)</span><span class="sxs-lookup"><span data-stu-id="e13b1-107">Items (Default)</span></span>

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="e13b1-108">LiteralItems</span><span class="sxs-lookup"><span data-stu-id="e13b1-108">LiteralItems</span></span>

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## <span data-ttu-id="e13b1-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e13b1-109">DESCRIPTION</span></span>

<span data-ttu-id="e13b1-110">De `Get-ChildItem` cmdlet haalt de items op een of meer opgegeven locaties op.</span><span class="sxs-lookup"><span data-stu-id="e13b1-110">The `Get-ChildItem` cmdlet gets the items in one or more specified locations.</span></span> <span data-ttu-id="e13b1-111">Als het item een container is, worden de items in de container opgehaald, ook wel onderliggende items genoemd.</span><span class="sxs-lookup"><span data-stu-id="e13b1-111">If the item is a container, it gets the items inside the container, known as child items.</span></span> <span data-ttu-id="e13b1-112">U kunt de para meter **recursieve** gebruiken om items in alle onderliggende containers op te halen en de para meter **Depth** gebruiken om het aantal niveaus te beperken dat moet worden herhaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-112">You can use the **Recurse** parameter to get items in all child containers and use the **Depth** parameter to limit the number of levels to recurse.</span></span>

<span data-ttu-id="e13b1-113">`Get-ChildItem` lege mappen worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-113">`Get-ChildItem` doesn't display empty directories.</span></span> <span data-ttu-id="e13b1-114">Wanneer een `Get-ChildItem` opdracht de **diepte** -of **recursieve** para meters bevat, worden lege mappen niet opgenomen in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e13b1-114">When a `Get-ChildItem` command includes the **Depth** or **Recurse** parameters, empty directories aren't included in the output.</span></span>

<span data-ttu-id="e13b1-115">Locaties worden blootgesteld aan `Get-ChildItem` door Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="e13b1-115">Locations are exposed to `Get-ChildItem` by PowerShell providers.</span></span> <span data-ttu-id="e13b1-116">Een locatie kan een map van een bestands systeem, een register component of een certificaat archief zijn.</span><span class="sxs-lookup"><span data-stu-id="e13b1-116">A location can be a file system directory, registry hive, or a certificate store.</span></span> <span data-ttu-id="e13b1-117">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-117">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e13b1-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e13b1-118">EXAMPLES</span></span>

### <span data-ttu-id="e13b1-119">Voor beeld 1: onderliggende items uit een bestandssysteem Directory ophalen</span><span class="sxs-lookup"><span data-stu-id="e13b1-119">Example 1: Get child items from a file system directory</span></span>

<span data-ttu-id="e13b1-120">In dit voor beeld worden de onderliggende items uit een map van het bestands systeem opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-120">This example gets the child items from a file system directory.</span></span> <span data-ttu-id="e13b1-121">De namen van de bestanden en mappen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-121">The filenames and subdirectory names are displayed.</span></span> <span data-ttu-id="e13b1-122">Voor lege locaties retourneert de opdracht geen uitvoer en keert deze terug naar de Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="e13b1-122">For empty locations, the command doesn't return any output and returns to the PowerShell prompt.</span></span>

<span data-ttu-id="e13b1-123">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map op te geven `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-123">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span>
<span data-ttu-id="e13b1-124">`Get-ChildItem` Hiermee worden de bestanden en mappen in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-124">`Get-ChildItem` displays the files and directories in the PowerShell console.</span></span>

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="e13b1-125">Standaard `Get-ChildItem` worden de modus ( **kenmerken** ), **LastWriteTime** , bestands grootte ( **lengte** ) en de **naam** van het item weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-125">By default `Get-ChildItem` lists the mode ( **Attributes** ), **LastWriteTime** , file size ( **Length** ), and the **Name** of the item.</span></span> <span data-ttu-id="e13b1-126">De letters in de **modus** eigenschap kunnen als volgt worden geïnterpreteerd:</span><span class="sxs-lookup"><span data-stu-id="e13b1-126">The letters in the **Mode** property can be interpreted as follows:</span></span>

- <span data-ttu-id="e13b1-127">`l` gekoppeld</span><span class="sxs-lookup"><span data-stu-id="e13b1-127">`l` (link)</span></span>
- <span data-ttu-id="e13b1-128">`d` uitvoermap</span><span class="sxs-lookup"><span data-stu-id="e13b1-128">`d` (directory)</span></span>
- <span data-ttu-id="e13b1-129">`a` faxberichten</span><span class="sxs-lookup"><span data-stu-id="e13b1-129">`a` (archive)</span></span>
- <span data-ttu-id="e13b1-130">`r` (alleen-lezen)</span><span class="sxs-lookup"><span data-stu-id="e13b1-130">`r` (read-only)</span></span>
- <span data-ttu-id="e13b1-131">`h` zit</span><span class="sxs-lookup"><span data-stu-id="e13b1-131">`h` (hidden)</span></span>
- <span data-ttu-id="e13b1-132">`s` (systeem).</span><span class="sxs-lookup"><span data-stu-id="e13b1-132">`s` (system).</span></span>

<span data-ttu-id="e13b1-133">Zie [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)voor meer informatie over de modus vlaggen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-133">For more information about the mode flags, see [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span></span>

### <span data-ttu-id="e13b1-134">Voor beeld 2: namen van onderliggende items in een directory ophalen</span><span class="sxs-lookup"><span data-stu-id="e13b1-134">Example 2: Get child item names in a directory</span></span>

<span data-ttu-id="e13b1-135">In dit voor beeld worden alleen de namen van items in een map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-135">This example lists only the names of items in a directory.</span></span>

<span data-ttu-id="e13b1-136">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map op te geven `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-136">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span> <span data-ttu-id="e13b1-137">De para meter **name** retourneert alleen de namen van bestanden of mappen uit het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="e13b1-137">The **Name** parameter returns only the file or directory names from the specified path.</span></span>

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### <span data-ttu-id="e13b1-138">Voor beeld 3: onderliggende items in de huidige map en submappen ophalen</span><span class="sxs-lookup"><span data-stu-id="e13b1-138">Example 3: Get child items in the current directory and subdirectories</span></span>

<span data-ttu-id="e13b1-139">In dit voor beeld worden **. txt** -bestanden weer gegeven die zich in de huidige map en de submappen ervan bevinden.</span><span class="sxs-lookup"><span data-stu-id="e13b1-139">This example displays **.txt** files that are located in the current directory and its subdirectories.</span></span>

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="e13b1-140">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om op te geven `C:\Test\*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-140">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify `C:\Test\*.txt`.</span></span> <span data-ttu-id="e13b1-141">**Pad** gebruikt het sterretje ( `*` )-Joker teken om alle bestanden met de bestandsnaam extensie op te geven `.txt` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-141">**Path** uses the asterisk (`*`) wildcard to specify all files with the filename extension `.txt`.</span></span> <span data-ttu-id="e13b1-142">De **recursieve** para meter zoekt in de map **pad** de submappen, zoals wordt weer gegeven in de **map:** koppen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-142">The **Recurse** parameter searches the **Path** directory its subdirectories, as shown in the **Directory:** headings.</span></span> <span data-ttu-id="e13b1-143">Met de para meter **Force** worden verborgen bestanden weer gegeven, zoals `hiddenfile.txt` een modus van **h**.</span><span class="sxs-lookup"><span data-stu-id="e13b1-143">The **Force** parameter displays hidden files such as `hiddenfile.txt` that have a mode of **h**.</span></span>

### <span data-ttu-id="e13b1-144">Voor beeld 4: onderliggende items ophalen met behulp van de para meter include</span><span class="sxs-lookup"><span data-stu-id="e13b1-144">Example 4: Get child items using the Include parameter</span></span>

<span data-ttu-id="e13b1-145">In dit voor beeld `Get-ChildItem` wordt de para meter **include** gebruikt om specifieke items te zoeken in de map die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-145">In this example `Get-ChildItem` uses the **Include** parameter to find specific items from the directory specified by the **Path** parameter.</span></span>

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="e13b1-146">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map **C:\Test** op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-146">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test**.</span></span> <span data-ttu-id="e13b1-147">De para meter **Path** bevat een asterisk ( `*` ) met het Joker teken () om de inhoud van de map op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-147">The **Path** parameter includes a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span>
<span data-ttu-id="e13b1-148">De para meter **include** maakt gebruik van een asterisk ( `*` ) als Joker teken om alle bestanden met de bestandsnaam extensie **. txt** op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-148">The **Include** parameter uses an asterisk (`*`) wildcard to specify all files with the file name extension **.txt**.</span></span>

<span data-ttu-id="e13b1-149">Wanneer de para meter **include** wordt gebruikt, moet de para meter **Path** een asterisk () met een sterretje ( `*` ) gebruiken om de inhoud van de map op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-149">When the **Include** parameter is used, the **Path** parameter needs a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span> <span data-ttu-id="e13b1-150">Bijvoorbeeld `-Path C:\Test\*`.</span><span class="sxs-lookup"><span data-stu-id="e13b1-150">For example, `-Path C:\Test\*`.</span></span>

- <span data-ttu-id="e13b1-151">Als de **recursie** -para meter wordt toegevoegd aan de opdracht, is de afsluitende asterisk ( `*` ) in de para meter **Path** optioneel.</span><span class="sxs-lookup"><span data-stu-id="e13b1-151">If the **Recurse** parameter is added to the command, the trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="e13b1-152">De **recursie** -para meter haalt items op uit de map **pad** en de bijbehorende submappen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-152">The **Recurse** parameter gets items from the **Path** directory and its subdirectories.</span></span> <span data-ttu-id="e13b1-153">bijvoorbeeld `-Path C:\Test\ -Recurse -Include *.txt`</span><span class="sxs-lookup"><span data-stu-id="e13b1-153">For example, `-Path C:\Test\ -Recurse -Include *.txt`</span></span>
- <span data-ttu-id="e13b1-154">Als een eindigend sterretje ( `*` ) niet is opgenomen in de para meter **Path** , retourneert de opdracht geen uitvoer en keert deze terug naar de Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="e13b1-154">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the command doesn't return any output and returns to the PowerShell prompt.</span></span> <span data-ttu-id="e13b1-155">Bijvoorbeeld `-Path C:\Test\`.</span><span class="sxs-lookup"><span data-stu-id="e13b1-155">For example, `-Path C:\Test\`.</span></span>

### <span data-ttu-id="e13b1-156">Voor beeld 5: onderliggende items ophalen met de para meter exclude</span><span class="sxs-lookup"><span data-stu-id="e13b1-156">Example 5: Get child items using the Exclude parameter</span></span>

<span data-ttu-id="e13b1-157">In de uitvoer van het voor beeld ziet u de inhoud van de map **C:\Test\Logs**.</span><span class="sxs-lookup"><span data-stu-id="e13b1-157">The example's output shows the contents of the directory **C:\Test\Logs**.</span></span> <span data-ttu-id="e13b1-158">De uitvoer is een verwijzing naar de andere opdrachten die gebruikmaken van de para meters **exclude** en **recursief** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-158">The output is a reference for the other commands that use the **Exclude** and **Recurse** parameters.</span></span>

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

<span data-ttu-id="e13b1-159">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map op te geven `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-159">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test\Logs`.</span></span>
<span data-ttu-id="e13b1-160">De para meter **exclude** maakt gebruik `*` van het Joker teken sterretje () om op te geven welke bestanden of mappen die met **een** of **een** beginnen, worden uitgesloten van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e13b1-160">The **Exclude** parameter uses the asterisk (`*`) wildcard to specify any files or directories that begin with **A** or **a** are excluded from the output.</span></span>

<span data-ttu-id="e13b1-161">Wanneer de **exclude** -para meter wordt gebruikt, is een sterretje ( `*` ) in de para meter **Path** optioneel.</span><span class="sxs-lookup"><span data-stu-id="e13b1-161">When the **Exclude** parameter is used, a trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="e13b1-162">Bijvoorbeeld `-Path C:\Test\Logs` of `-Path C:\Test\Logs\*`.</span><span class="sxs-lookup"><span data-stu-id="e13b1-162">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span>

- <span data-ttu-id="e13b1-163">Als een eindigend sterretje ( `*` ) niet is opgenomen in de para meter **Path** , wordt de inhoud van de para meter **Path** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-163">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="e13b1-164">De uitzonde ringen zijn bestands namen of mapnamen die overeenkomen met de waarde van de para meter **exclude** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-164">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="e13b1-165">Als een eindigend sterretje ( `*` ) wordt opgenomen in de para meter **Path** , wordt de opdracht herhaald in de para meters van het **pad** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-165">If a trailing asterisk (`*`) is included in the **Path** parameter, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="e13b1-166">De uitzonde ringen zijn bestands namen of mapnamen die overeenkomen met de waarde van de para meter **exclude** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-166">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="e13b1-167">Als de **recursie** -para meter wordt toegevoegd aan de opdracht, is de uitvoer van de recursie hetzelfde, ongeacht of de para meter **Path** een afsluitend sterretje ( `*` ) bevat.</span><span class="sxs-lookup"><span data-stu-id="e13b1-167">If the **Recurse** parameter is added to the command, the recursion output is the same whether or not the **Path** parameter includes a trailing asterisk (`*`).</span></span>

### <span data-ttu-id="e13b1-168">Voor beeld 6: de register sleutels ophalen uit een register component</span><span class="sxs-lookup"><span data-stu-id="e13b1-168">Example 6: Get the registry keys from a registry hive</span></span>

<span data-ttu-id="e13b1-169">In dit voor beeld worden alle register sleutels opgehaald uit `HKEY_LOCAL_MACHINE\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-169">This example gets all the registry keys from `HKEY_LOCAL_MACHINE\HARDWARE`.</span></span>

<span data-ttu-id="e13b1-170">`Get-ChildItem` maakt gebruik van de para meter **Path** om de register sleutel op te geven `HKLM:\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-170">`Get-ChildItem` uses the **Path** parameter to specify the registry key `HKLM:\HARDWARE`.</span></span> <span data-ttu-id="e13b1-171">Het pad en het hoogste niveau van register sleutels van de Hive worden weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="e13b1-171">The hive's path and top level of registry keys are displayed in the PowerShell console.</span></span>

<span data-ttu-id="e13b1-172">Zie [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-172">For more information, see [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span></span>

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

<span data-ttu-id="e13b1-173">Met de eerste opdracht wordt de inhoud van de `HKLM:\HARDWARE` register sleutel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-173">The first command shows the contents of the `HKLM:\HARDWARE` registry key.</span></span> <span data-ttu-id="e13b1-174">De **exclude** -para meter geeft `Get-ChildItem` aan dat er geen subsleutels worden geretourneerd die beginnen met `D*` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-174">The **Exclude** parameter tells `Get-ChildItem` not to return any subkeys that start with `D*`.</span></span> <span data-ttu-id="e13b1-175">Op dit moment werkt de **exclude** -para meter alleen voor subsleutels, niet voor item eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-175">Currently, the **Exclude** parameter only works on subkeys, not item properties.</span></span>

### <span data-ttu-id="e13b1-176">Voor beeld 7: alle certificaten ophalen met de instantie voor ondertekening van programma code</span><span class="sxs-lookup"><span data-stu-id="e13b1-176">Example 7: Get all certificates with code-signing authority</span></span>

<span data-ttu-id="e13b1-177">In dit voor beeld wordt elk certificaat opgehaald uit het Power shell- **certificaat:** station met instantie voor ondertekening van programma code.</span><span class="sxs-lookup"><span data-stu-id="e13b1-177">This example gets each certificate in the PowerShell **Cert:** drive that has code-signing authority.</span></span>

<span data-ttu-id="e13b1-178">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om het **certificaat:** provider op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-178">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the **Cert:** provider.</span></span> <span data-ttu-id="e13b1-179">De **recursieve** para meter doorzoekt de map die is opgegeven door het **pad** en de bijbehorende submappen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-179">The **Recurse** parameter searches the directory specified by **Path** and its subdirectories.</span></span> <span data-ttu-id="e13b1-180">Met de para meter **CodeSigningCert** worden alleen certificaten opgehaald die instantie voor ondertekening van programma code hebben.</span><span class="sxs-lookup"><span data-stu-id="e13b1-180">The **CodeSigningCert** parameter gets only certificates that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

<span data-ttu-id="e13b1-181">Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie over de certificaat provider en het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="e13b1-181">For more information about the Certificate provider and the Cert: drive, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="e13b1-182">Voor beeld 8: items ophalen met de para meter Depth</span><span class="sxs-lookup"><span data-stu-id="e13b1-182">Example 8: Get items using the Depth parameter</span></span>

<span data-ttu-id="e13b1-183">In dit voor beeld worden de items in een map en de bijbehorende submappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-183">This example displays the items in a directory and its subdirectories.</span></span> <span data-ttu-id="e13b1-184">De **Depth** -para meter bepaalt het aantal niveaus van de submap dat moet worden meegenomen in de recursie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-184">The **Depth** parameter determines the number of subdirectory levels to include in the recursion.</span></span> <span data-ttu-id="e13b1-185">Lege mappen worden uitgesloten van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e13b1-185">Empty directories are excluded from the output.</span></span>

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

<span data-ttu-id="e13b1-186">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om **C:\Parent** op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-186">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify **C:\Parent**.</span></span> <span data-ttu-id="e13b1-187">Met de **diepte** parameter worden twee niveaus van recursie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-187">The **Depth** parameter specifies two levels of recursion.</span></span> <span data-ttu-id="e13b1-188">`Get-ChildItem` geeft de inhoud weer van de map die is opgegeven door de para meter **Path** en de twee niveaus van submappen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-188">`Get-ChildItem` displays the contents of the directory specified by the **Path** parameter and the two levels of subdirectories.</span></span>

### <span data-ttu-id="e13b1-189">Voor beeld 9: informatie over vaste koppeling ophalen</span><span class="sxs-lookup"><span data-stu-id="e13b1-189">Example 9: Getting hard link information</span></span>

<span data-ttu-id="e13b1-190">In Power shell 6,2 is een alternatieve weer gave toegevoegd voor het ophalen van harde koppelings informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-190">In PowerShell 6.2, an alternate view was added to get hard link information.</span></span>

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### <span data-ttu-id="e13b1-191">Voor beeld 9: uitvoer voor experimentele functie PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="e13b1-191">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="e13b1-192">In Power shell 7 op UNIX-systemen biedt de experimentele functie **PSUnixFileStat** UNIX-achtige uitvoer:</span><span class="sxs-lookup"><span data-stu-id="e13b1-192">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

<span data-ttu-id="e13b1-193">De nieuwe eigenschappen die nu deel uitmaken van de uitvoer zijn:</span><span class="sxs-lookup"><span data-stu-id="e13b1-193">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="e13b1-194">**UnixMode** is de bestands machtigingen die worden weer gegeven op een UNIX-systeem</span><span class="sxs-lookup"><span data-stu-id="e13b1-194">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="e13b1-195">De **gebruiker** is de bestands eigenaar</span><span class="sxs-lookup"><span data-stu-id="e13b1-195">**User** is the file owner</span></span>
- <span data-ttu-id="e13b1-196">**Groep** is de eigenaar van de groep</span><span class="sxs-lookup"><span data-stu-id="e13b1-196">**Group** is the group owner</span></span>
- <span data-ttu-id="e13b1-197">**Grootte** is de grootte van het bestand of de map zoals deze wordt weer gegeven op een UNIX-systeem</span><span class="sxs-lookup"><span data-stu-id="e13b1-197">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="e13b1-198">Parameters</span><span class="sxs-lookup"><span data-stu-id="e13b1-198">Parameters</span></span>

### <span data-ttu-id="e13b1-199">-Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e13b1-199">-Attributes</span></span>

<span data-ttu-id="e13b1-200">Hiermee worden bestanden en mappen opgehaald met de opgegeven kenmerken.</span><span class="sxs-lookup"><span data-stu-id="e13b1-200">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="e13b1-201">Deze para meter ondersteunt alle kenmerken en geeft u de mogelijkheid om complexe combi Naties van kenmerken op te geven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-201">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="e13b1-202">Als u bijvoorbeeld niet-systeem bestanden (niet directory's) wilt ophalen die zijn versleuteld of gecomprimeerd, typt u:</span><span class="sxs-lookup"><span data-stu-id="e13b1-202">For example, to get non-system files (not directories) that are encrypted or compressed, type:</span></span>

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

<span data-ttu-id="e13b1-203">Als u bestanden en mappen met veelgebruikte kenmerken wilt zoeken, gebruikt u de para meter **Attributes** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-203">To find files and folders with commonly used attributes, use the **Attributes** parameter.</span></span> <span data-ttu-id="e13b1-204">Of de para meters **map** , **bestand** , **verborgen** , **alleen-lezen** en **systeem**.</span><span class="sxs-lookup"><span data-stu-id="e13b1-204">Or, the parameters **Directory** , **File** , **Hidden** , **ReadOnly** , and **System**.</span></span>

<span data-ttu-id="e13b1-205">De para meter **Attributes** ondersteunt de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="e13b1-205">The **Attributes** parameter supports the following properties:</span></span>

- <span data-ttu-id="e13b1-206">**Archiveren**</span><span class="sxs-lookup"><span data-stu-id="e13b1-206">**Archive**</span></span>
- <span data-ttu-id="e13b1-207">**Gecomprimeerd**</span><span class="sxs-lookup"><span data-stu-id="e13b1-207">**Compressed**</span></span>
- <span data-ttu-id="e13b1-208">**Apparaat**</span><span class="sxs-lookup"><span data-stu-id="e13b1-208">**Device**</span></span>
- <span data-ttu-id="e13b1-209">**Directory**</span><span class="sxs-lookup"><span data-stu-id="e13b1-209">**Directory**</span></span>
- <span data-ttu-id="e13b1-210">**Versleuteld**</span><span class="sxs-lookup"><span data-stu-id="e13b1-210">**Encrypted**</span></span>
- <span data-ttu-id="e13b1-211">**Verborgen**</span><span class="sxs-lookup"><span data-stu-id="e13b1-211">**Hidden**</span></span>
- <span data-ttu-id="e13b1-212">**IntegrityStream**</span><span class="sxs-lookup"><span data-stu-id="e13b1-212">**IntegrityStream**</span></span>
- <span data-ttu-id="e13b1-213">**Normaal**</span><span class="sxs-lookup"><span data-stu-id="e13b1-213">**Normal**</span></span>
- <span data-ttu-id="e13b1-214">**NoScrubData**</span><span class="sxs-lookup"><span data-stu-id="e13b1-214">**NoScrubData**</span></span>
- <span data-ttu-id="e13b1-215">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="e13b1-215">**NotContentIndexed**</span></span>
- <span data-ttu-id="e13b1-216">**Offline**</span><span class="sxs-lookup"><span data-stu-id="e13b1-216">**Offline**</span></span>
- <span data-ttu-id="e13b1-217">**Kenmerk**</span><span class="sxs-lookup"><span data-stu-id="e13b1-217">**ReadOnly**</span></span>
- <span data-ttu-id="e13b1-218">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="e13b1-218">**ReparsePoint**</span></span>
- <span data-ttu-id="e13b1-219">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="e13b1-219">**SparseFile**</span></span>
- <span data-ttu-id="e13b1-220">**Systeem**</span><span class="sxs-lookup"><span data-stu-id="e13b1-220">**System**</span></span>
- <span data-ttu-id="e13b1-221">**Tijdelijk**</span><span class="sxs-lookup"><span data-stu-id="e13b1-221">**Temporary**</span></span>

<span data-ttu-id="e13b1-222">Zie de [FileAttributes-inventarisatie](/dotnet/api/system.io.fileattributes)voor een beschrijving van deze kenmerken.</span><span class="sxs-lookup"><span data-stu-id="e13b1-222">For a description of these attributes, see the [FileAttributes Enumeration](/dotnet/api/system.io.fileattributes).</span></span>

<span data-ttu-id="e13b1-223">Als u kenmerken wilt combi neren, gebruikt u de volgende Opera tors:</span><span class="sxs-lookup"><span data-stu-id="e13b1-223">To combine attributes, use the following operators:</span></span>

- <span data-ttu-id="e13b1-224">`!` TEN</span><span class="sxs-lookup"><span data-stu-id="e13b1-224">`!` (NOT)</span></span>
- <span data-ttu-id="e13b1-225">`+` MAAR</span><span class="sxs-lookup"><span data-stu-id="e13b1-225">`+` (AND)</span></span>
- <span data-ttu-id="e13b1-226">`,` OF</span><span class="sxs-lookup"><span data-stu-id="e13b1-226">`,` (OR)</span></span>

<span data-ttu-id="e13b1-227">Gebruik geen spaties tussen een operator en het bijbehorende kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e13b1-227">Don't use spaces between an operator and its attribute.</span></span> <span data-ttu-id="e13b1-228">Spaties worden geaccepteerd na komma's.</span><span class="sxs-lookup"><span data-stu-id="e13b1-228">Spaces are accepted after commas.</span></span>

<span data-ttu-id="e13b1-229">Voor algemene kenmerken gebruikt u de volgende afkortingen:</span><span class="sxs-lookup"><span data-stu-id="e13b1-229">For common attributes, use the following abbreviations:</span></span>

- <span data-ttu-id="e13b1-230">`D` Uitvoermap</span><span class="sxs-lookup"><span data-stu-id="e13b1-230">`D` (Directory)</span></span>
- <span data-ttu-id="e13b1-231">`H` Zit</span><span class="sxs-lookup"><span data-stu-id="e13b1-231">`H` (Hidden)</span></span>
- <span data-ttu-id="e13b1-232">`R` (Alleen-lezen)</span><span class="sxs-lookup"><span data-stu-id="e13b1-232">`R` (Read-only)</span></span>
- <span data-ttu-id="e13b1-233">`S` Opgehaald</span><span class="sxs-lookup"><span data-stu-id="e13b1-233">`S` (System)</span></span>

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-234">-Diepte</span><span class="sxs-lookup"><span data-stu-id="e13b1-234">-Depth</span></span>

<span data-ttu-id="e13b1-235">Deze para meter is toegevoegd in Power shell 5,0 en stelt u in staat om de diepte van recursie te bepalen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-235">This parameter was added in PowerShell 5.0 and enables you to control the depth of recursion.</span></span> <span data-ttu-id="e13b1-236">`Get-ChildItem`De inhoud van de bovenliggende map wordt standaard weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-236">By default, `Get-ChildItem` displays the contents of the parent directory.</span></span> <span data-ttu-id="e13b1-237">De **Depth** para meter bepaalt het aantal niveaus van de submap die zijn opgenomen in de recursie en geeft de inhoud weer.</span><span class="sxs-lookup"><span data-stu-id="e13b1-237">The **Depth** parameter determines the number of subdirectory levels that are included in the recursion and displays the contents.</span></span>

<span data-ttu-id="e13b1-238">U kunt bijvoorbeeld `Depth 2` de para meter **Path** , het eerste niveau van submappen en het tweede niveau van submappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="e13b1-238">For example, `Depth 2` includes the **Path** parameter's directory, first level of subdirectories, and second level of subdirectories.</span></span> <span data-ttu-id="e13b1-239">Standaard worden mapnamen en bestands namen in de uitvoer opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-239">By default directory names and filenames are included in the output.</span></span>

> [!NOTE]
> <span data-ttu-id="e13b1-240">Op een Windows-computer in Power shell of **cmd.exe** , kunt u een grafische weer gave van een mapstructuur weer geven met de opdracht **tree.com** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-240">On a Windows computer from PowerShell or **cmd.exe** , you can display a graphical view of a directory structure with the **tree.com** command.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-241">-Directory</span><span class="sxs-lookup"><span data-stu-id="e13b1-241">-Directory</span></span>

<span data-ttu-id="e13b1-242">Als u een lijst met mappen wilt ophalen, gebruikt u de para meter **Directory** of de para meter **Attributes** met de **Directory** -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e13b1-242">To get a list of directories, use the **Directory** parameter or the **Attributes** parameter with the **Directory** property.</span></span> <span data-ttu-id="e13b1-243">U kunt de para meter **recursief** gebruiken met **Directory**.</span><span class="sxs-lookup"><span data-stu-id="e13b1-243">You can use the **Recurse** parameter with **Directory**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-244">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="e13b1-244">-Exclude</span></span>

<span data-ttu-id="e13b1-245">Hiermee geeft u als een teken reeks matrix een eigenschap of eigenschap op die met deze cmdlet wordt uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="e13b1-245">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="e13b1-246">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-246">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e13b1-247">Voer een element of patroon van een pad in, zoals `*.txt` of `A*` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-247">Enter a path element or pattern, such as `*.txt` or `A*`.</span></span> <span data-ttu-id="e13b1-248">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="e13b1-248">Wildcard characters are accepted.</span></span>

<span data-ttu-id="e13b1-249">Een eindigend sterretje ( `*` ) in de para meter **Path** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="e13b1-249">A trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="e13b1-250">Bijvoorbeeld `-Path C:\Test\Logs` of `-Path C:\Test\Logs\*`.</span><span class="sxs-lookup"><span data-stu-id="e13b1-250">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span> <span data-ttu-id="e13b1-251">Als er een sterretje ( `*` ) wordt opgenomen, wordt de opdracht herhaald in de para meters van het **pad** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-251">If a trailing asterisk (`*`) is included, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="e13b1-252">Zonder sterretje ( `*` ) wordt de inhoud van de para meter **Path** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-252">Without the asterisk (`*`), the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="e13b1-253">Meer informatie is opgenomen in voor beeld 5 en de sectie opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-253">More details are included in Example 5 and the Notes section.</span></span>

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

### <span data-ttu-id="e13b1-254">-Bestand</span><span class="sxs-lookup"><span data-stu-id="e13b1-254">-File</span></span>

<span data-ttu-id="e13b1-255">Als u een lijst met bestanden wilt ophalen, gebruikt u de para meter **File** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-255">To get a list of files, use the **File** parameter.</span></span> <span data-ttu-id="e13b1-256">U kunt de **recursieve** para meter gebruiken met **bestand**.</span><span class="sxs-lookup"><span data-stu-id="e13b1-256">You can use the **Recurse** parameter with **File**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-257">-Filter</span><span class="sxs-lookup"><span data-stu-id="e13b1-257">-Filter</span></span>

<span data-ttu-id="e13b1-258">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="e13b1-258">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="e13b1-259">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="e13b1-259">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="e13b1-260">Filters zijn efficiënter dan andere para meters.</span><span class="sxs-lookup"><span data-stu-id="e13b1-260">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="e13b1-261">De provider past filter toe wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-261">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="e13b1-262">De filter teken reeks wordt door gegeven aan de .NET API om bestanden te inventariseren.</span><span class="sxs-lookup"><span data-stu-id="e13b1-262">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="e13b1-263">De API ondersteunt alleen `*` en `?` joker tekens.</span><span class="sxs-lookup"><span data-stu-id="e13b1-263">The API only supports `*` and `?` wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e13b1-264">-FollowSymlink</span><span class="sxs-lookup"><span data-stu-id="e13b1-264">-FollowSymlink</span></span>

<span data-ttu-id="e13b1-265">Standaard worden in de `Get-ChildItem` cmdlet symbolische koppelingen weer gegeven naar directory's die zijn gevonden tijdens de recursie, maar worden ze niet meer in deze mappen opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-265">By default, the `Get-ChildItem` cmdlet displays symbolic links to directories found during recursion, but doesn't recurse into them.</span></span> <span data-ttu-id="e13b1-266">Gebruik de para meter **FollowSymlink** om te zoeken in de mappen waarin deze symbolische koppelingen zijn gericht.</span><span class="sxs-lookup"><span data-stu-id="e13b1-266">Use the **FollowSymlink** parameter to search the directories that target those symbolic links.</span></span> <span data-ttu-id="e13b1-267">De **FollowSymlink** is een dynamische para meter en wordt alleen ondersteund in de **File System** provider.</span><span class="sxs-lookup"><span data-stu-id="e13b1-267">The **FollowSymlink** is a dynamic parameter and is supported only in the **FileSystem** provider.</span></span>

<span data-ttu-id="e13b1-268">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e13b1-268">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="e13b1-269">-Force</span><span class="sxs-lookup"><span data-stu-id="e13b1-269">-Force</span></span>

<span data-ttu-id="e13b1-270">Hiermee kan de cmdlet items ophalen die anders niet toegankelijk zijn voor de gebruiker, zoals verborgen of systeem bestanden.</span><span class="sxs-lookup"><span data-stu-id="e13b1-270">Allows the cmdlet to get items that otherwise can't be accessed by the user, such as hidden or system files.</span></span> <span data-ttu-id="e13b1-271">De para meter **Force** overschrijft geen beveiligings beperkingen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-271">The **Force** parameter doesn't override security restrictions.</span></span> <span data-ttu-id="e13b1-272">Implementatie is afhankelijk van providers.</span><span class="sxs-lookup"><span data-stu-id="e13b1-272">Implementation varies among providers.</span></span> <span data-ttu-id="e13b1-273">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-273">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="e13b1-274">-Verborgen</span><span class="sxs-lookup"><span data-stu-id="e13b1-274">-Hidden</span></span>

<span data-ttu-id="e13b1-275">Als u alleen verborgen items wilt ophalen, gebruikt u de para meter **Hidden** of de para meter **Attributes** met de eigenschap **Hidden** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-275">To get only hidden items, use the **Hidden** parameter or the **Attributes** parameter with the **Hidden** property.</span></span> <span data-ttu-id="e13b1-276">Standaard worden `Get-ChildItem` verborgen items niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-276">By default, `Get-ChildItem` doesn't display hidden items.</span></span> <span data-ttu-id="e13b1-277">Gebruik de para meter **Force** om verborgen items te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-277">Use the **Force** parameter to get hidden items.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-278">-Include</span><span class="sxs-lookup"><span data-stu-id="e13b1-278">-Include</span></span>

<span data-ttu-id="e13b1-279">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-279">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="e13b1-280">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-280">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e13b1-281">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-281">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="e13b1-282">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e13b1-282">Wildcard characters are permitted.</span></span> <span data-ttu-id="e13b1-283">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="e13b1-283">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="e13b1-284">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e13b1-284">-LiteralPath</span></span>

<span data-ttu-id="e13b1-285">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="e13b1-285">Specifies a path to one or more locations.</span></span> <span data-ttu-id="e13b1-286">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="e13b1-286">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="e13b1-287">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="e13b1-287">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e13b1-288">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="e13b1-288">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e13b1-289">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-289">Single quotation marks tell PowerShell to not interpret any characters as escape sequences.</span></span>

<span data-ttu-id="e13b1-290">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-290">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-291">-Name</span><span class="sxs-lookup"><span data-stu-id="e13b1-291">-Name</span></span>

<span data-ttu-id="e13b1-292">Hiermee worden alleen de namen van de items in de locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-292">Gets only the names of the items in the location.</span></span> <span data-ttu-id="e13b1-293">De uitvoer is een teken reeks object dat via de pijp lijn naar andere opdrachten kan worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="e13b1-293">The output is a string object that can be sent down the pipeline to other commands.</span></span> <span data-ttu-id="e13b1-294">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e13b1-294">Wildcards are permitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e13b1-295">-Path</span><span class="sxs-lookup"><span data-stu-id="e13b1-295">-Path</span></span>

<span data-ttu-id="e13b1-296">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="e13b1-296">Specifies a path to one or more locations.</span></span> <span data-ttu-id="e13b1-297">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="e13b1-297">Wildcards are accepted.</span></span> <span data-ttu-id="e13b1-298">De standaard locatie is de huidige map ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="e13b1-298">The default location is the current directory (`.`).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="e13b1-299">-ReadOnly</span><span class="sxs-lookup"><span data-stu-id="e13b1-299">-ReadOnly</span></span>

<span data-ttu-id="e13b1-300">Als u alleen-lezen items wilt ophalen, gebruikt u de para meter **ReadOnly** of de **eigenschap para meter kenmerk** **ReadOnly** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-300">To get only read-only items, use the **ReadOnly** parameter or the **Attributes** parameter **ReadOnly** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-301">-Recursief</span><span class="sxs-lookup"><span data-stu-id="e13b1-301">-Recurse</span></span>

<span data-ttu-id="e13b1-302">Hiermee worden de items in de opgegeven locaties en alle onderliggende items van de locaties opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-302">Gets the items in the specified locations and in all child items of the locations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-303">-Systeem</span><span class="sxs-lookup"><span data-stu-id="e13b1-303">-System</span></span>

<span data-ttu-id="e13b1-304">Hiermee worden alleen systeem bestanden en mappen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b1-304">Gets only system files and directories.</span></span> <span data-ttu-id="e13b1-305">Als u alleen systeem bestanden en-mappen wilt ophalen, gebruikt u de para meter **systeem** -of **kenmerk** parameter **systeem** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e13b1-305">To get only system files and folders, use the **System** parameter or **Attributes** parameter **System** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e13b1-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e13b1-306">CommonParameters</span></span>

<span data-ttu-id="e13b1-307">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e13b1-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e13b1-308">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e13b1-309">INVOER</span><span class="sxs-lookup"><span data-stu-id="e13b1-309">INPUTS</span></span>

### <span data-ttu-id="e13b1-310">System. String</span><span class="sxs-lookup"><span data-stu-id="e13b1-310">System.String</span></span>

<span data-ttu-id="e13b1-311">U kunt een teken reeks met een pad naar door sluizen `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-311">You can pipe a string that contains a path to `Get-ChildItem`.</span></span>

## <span data-ttu-id="e13b1-312">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e13b1-312">OUTPUTS</span></span>

### <span data-ttu-id="e13b1-313">System. object</span><span class="sxs-lookup"><span data-stu-id="e13b1-313">System.Object</span></span>

<span data-ttu-id="e13b1-314">Het type van het object dat `Get-ChildItem` retourneert, wordt bepaald door de objecten in het pad van de provider-schijf.</span><span class="sxs-lookup"><span data-stu-id="e13b1-314">The type of object that `Get-ChildItem` returns is determined by the objects in the provider drive path.</span></span>

### <span data-ttu-id="e13b1-315">System. String</span><span class="sxs-lookup"><span data-stu-id="e13b1-315">System.String</span></span>

<span data-ttu-id="e13b1-316">Als u de para meter **name** gebruikt, `Get-ChildItem` retourneert de object namen als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="e13b1-316">If you use the **Name** parameter, `Get-ChildItem` returns the object names as strings.</span></span>

## <span data-ttu-id="e13b1-317">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e13b1-317">NOTES</span></span>

- <span data-ttu-id="e13b1-318">`Get-ChildItem` kan worden uitgevoerd met een van de ingebouwde aliassen, `ls` , `dir` en `gci` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-318">`Get-ChildItem` can be run using any of the built-in aliases, `ls`, `dir`, and `gci`.</span></span> <span data-ttu-id="e13b1-319">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-319">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="e13b1-320">`Get-ChildItem` Standaard worden verborgen items niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-320">`Get-ChildItem` doesn't get hidden items by default.</span></span> <span data-ttu-id="e13b1-321">Als u verborgen items wilt ophalen, gebruikt u de para meter **Forces** .</span><span class="sxs-lookup"><span data-stu-id="e13b1-321">To get hidden items, use the **Force** parameter.</span></span>
- <span data-ttu-id="e13b1-322">De `Get-ChildItem` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b1-322">The `Get-ChildItem` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e13b1-323">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="e13b1-323">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="e13b1-324">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e13b1-324">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e13b1-325">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e13b1-325">RELATED LINKS</span></span>

[<span data-ttu-id="e13b1-326">about_Certificate_Provider</span><span class="sxs-lookup"><span data-stu-id="e13b1-326">about_Certificate_Provider</span></span>](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[<span data-ttu-id="e13b1-327">about_Providers</span><span class="sxs-lookup"><span data-stu-id="e13b1-327">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="e13b1-328">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="e13b1-328">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="e13b1-329">about_Registry_Provider</span><span class="sxs-lookup"><span data-stu-id="e13b1-329">about_Registry_Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[<span data-ttu-id="e13b1-330">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="e13b1-330">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="e13b1-331">Get-alias</span><span class="sxs-lookup"><span data-stu-id="e13b1-331">Get-Alias</span></span>](../Microsoft.PowerShell.Utility/Get-Alias.md)

[<span data-ttu-id="e13b1-332">Get-item</span><span class="sxs-lookup"><span data-stu-id="e13b1-332">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="e13b1-333">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="e13b1-333">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="e13b1-334">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e13b1-334">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="e13b1-335">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e13b1-335">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="e13b1-336">Split-pad</span><span class="sxs-lookup"><span data-stu-id="e13b1-336">Split-Path</span></span>](Split-Path.md)

