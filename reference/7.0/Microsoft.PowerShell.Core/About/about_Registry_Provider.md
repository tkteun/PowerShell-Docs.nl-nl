---
description: Register
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register provider
ms.openlocfilehash: efed68c42d46d5a44864af6b8892413c680c6b4e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252173"
---
# <a name="registry-provider"></a><span data-ttu-id="c0077-104">Register provider</span><span class="sxs-lookup"><span data-stu-id="c0077-104">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="c0077-105">Provider naam</span><span class="sxs-lookup"><span data-stu-id="c0077-105">Provider name</span></span>

<span data-ttu-id="c0077-106">Register</span><span class="sxs-lookup"><span data-stu-id="c0077-106">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="c0077-107">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="c0077-107">Drives</span></span>

<span data-ttu-id="c0077-108">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="c0077-108">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="c0077-109">Functies</span><span class="sxs-lookup"><span data-stu-id="c0077-109">Capabilities</span></span>

<span data-ttu-id="c0077-110">**ShouldProcess** , **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="c0077-110">**ShouldProcess** , **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="c0077-111">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0077-111">Short description</span></span>

<span data-ttu-id="c0077-112">Biedt toegang tot de register sleutels, vermeldingen en waarden in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c0077-112">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="c0077-113">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0077-113">Detailed description</span></span>

<span data-ttu-id="c0077-114">Met de Power shell- **register** provider kunt u register sleutels, vermeldingen en waarden in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c0077-114">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="c0077-115">De **register** stations zijn een hiërarchische naam ruimte met de register sleutels en subsleutels op uw computer.</span><span class="sxs-lookup"><span data-stu-id="c0077-115">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="c0077-116">Register vermeldingen en-waarden zijn geen onderdelen van die hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="c0077-116">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="c0077-117">In plaats daarvan zijn ze eigenschappen van elk van de sleutels.</span><span class="sxs-lookup"><span data-stu-id="c0077-117">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="c0077-118">De **register** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="c0077-118">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="c0077-119">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="c0077-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="c0077-120">Set-Location</span><span class="sxs-lookup"><span data-stu-id="c0077-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="c0077-121">Get-item</span><span class="sxs-lookup"><span data-stu-id="c0077-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="c0077-122">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="c0077-122">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="c0077-123">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="c0077-123">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="c0077-124">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c0077-124">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="c0077-125">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="c0077-125">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="c0077-126">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="c0077-126">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="c0077-127">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-127">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="c0077-128">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-128">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="c0077-129">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-129">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="c0077-130">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-130">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="c0077-131">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="c0077-131">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="c0077-132">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="c0077-132">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="c0077-133">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="c0077-133">Types exposed by this provider</span></span>

<span data-ttu-id="c0077-134">Register sleutels worden weer gegeven als exemplaren van de klasse [micro soft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) .</span><span class="sxs-lookup"><span data-stu-id="c0077-134">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="c0077-135">Register vermeldingen worden weer gegeven als exemplaren van de klasse [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .</span><span class="sxs-lookup"><span data-stu-id="c0077-135">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="c0077-136">Navigeren door de register stations</span><span class="sxs-lookup"><span data-stu-id="c0077-136">Navigating the Registry drives</span></span>

<span data-ttu-id="c0077-137">De gegevens opslag van de **register** provider is beschikbaar als twee standaard stations.</span><span class="sxs-lookup"><span data-stu-id="c0077-137">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="c0077-138">De register locatie HKEY_LOCAL_MACHINE wordt toegewezen aan het `HKLM:` station en HKEY_CURRENT_USER wordt toegewezen aan het `HKCU:` station.</span><span class="sxs-lookup"><span data-stu-id="c0077-138">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="c0077-139">Als u wilt werken met het REGI ster, kunt u uw locatie wijzigen in het `HKLM:` station met behulp van de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="c0077-139">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="c0077-140">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="c0077-140">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="c0077-141">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c0077-141">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="c0077-142">U kunt ook met de **register** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="c0077-142">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="c0077-143">Als u wilt verwijzen naar een register sleutel van een andere locatie, gebruikt u de naam van het station ( `HKLM:` , `HKCU:` ) in het pad.</span><span class="sxs-lookup"><span data-stu-id="c0077-143">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="c0077-144">Gebruik een back slash ( \\ ) of een slash (/) om een niveau van het **register** station aan te geven.</span><span class="sxs-lookup"><span data-stu-id="c0077-144">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="c0077-145">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="c0077-145">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="c0077-146">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="c0077-146">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="c0077-147">Dit laatste voor beeld toont een andere pad-syntaxis die u kunt gebruiken om te navigeren door de **register** provider.</span><span class="sxs-lookup"><span data-stu-id="c0077-147">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="c0077-148">Deze syntaxis maakt gebruik van de provider naam, gevolgd door twee dubbele punten `::` .</span><span class="sxs-lookup"><span data-stu-id="c0077-148">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="c0077-149">Met deze syntaxis kunt u de volledige HIVE-naam gebruiken in plaats van de naam van het toegewezen station `HKLM` .</span><span class="sxs-lookup"><span data-stu-id="c0077-149">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="c0077-150">De inhoud van register sleutels weer geven</span><span class="sxs-lookup"><span data-stu-id="c0077-150">Displaying the contents of registry keys</span></span>

<span data-ttu-id="c0077-151">Het REGI ster is onderverdeeld in sleutels, subsleutels en vermeldingen.</span><span class="sxs-lookup"><span data-stu-id="c0077-151">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="c0077-152">Zie [structuur van het REGI ster](/windows/desktop/sysinfo/structure-of-the-registry)voor meer informatie over de Register structuur.</span><span class="sxs-lookup"><span data-stu-id="c0077-152">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="c0077-153">In een **register** station is elke sleutel een container.</span><span class="sxs-lookup"><span data-stu-id="c0077-153">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="c0077-154">Een sleutel kan een wille keurig aantal sleutels bevatten.</span><span class="sxs-lookup"><span data-stu-id="c0077-154">A key can contain any number of keys.</span></span> <span data-ttu-id="c0077-155">Een register sleutel met een bovenliggende sleutel wordt een subsleutel genoemd.</span><span class="sxs-lookup"><span data-stu-id="c0077-155">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="c0077-156">U kunt gebruiken `Get-ChildItem` om register sleutels weer te geven en naar `Set-Location` een sleutelpad te navigeren.</span><span class="sxs-lookup"><span data-stu-id="c0077-156">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="c0077-157">Register waarden zijn kenmerken van een register sleutel.</span><span class="sxs-lookup"><span data-stu-id="c0077-157">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="c0077-158">In het **register** station worden deze **item eigenschappen** genoemd.</span><span class="sxs-lookup"><span data-stu-id="c0077-158">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="c0077-159">Een register sleutel kan zowel onderliggende sleutels als item eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="c0077-159">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="c0077-160">In dit voor beeld wordt het verschil tussen `Get-Item` en `Get-ChildItem` weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0077-160">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="c0077-161">Wanneer u `Get-Item` op de register sleutel ' spooler ' gebruikt, kunt u de eigenschappen ervan weer geven.</span><span class="sxs-lookup"><span data-stu-id="c0077-161">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="c0077-162">Elke register sleutel kan ook subsleutels hebben.</span><span class="sxs-lookup"><span data-stu-id="c0077-162">Each registry key can also have subkeys.</span></span> <span data-ttu-id="c0077-163">Wanneer u `Get-Item` een register sleutel gebruikt, worden de subsleutels niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0077-163">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="c0077-164">`Get-ChildItem`Met de cmdlet worden de onderliggende items van de ' spooler-sleutel ' weer gegeven, inclusief de eigenschappen van elke subsleutel.</span><span class="sxs-lookup"><span data-stu-id="c0077-164">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="c0077-165">De eigenschappen van de bovenliggende sleutels worden niet weer gegeven wanneer u gebruikt `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="c0077-165">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="c0077-166">De `Get-Item` cmdlet kan ook worden gebruikt op de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="c0077-166">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="c0077-167">In het volgende voor beeld wordt naar de register sleutel ' spooler ' genavigeerd en worden de item eigenschappen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c0077-167">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="c0077-168">De punt `.` wordt gebruikt om de huidige locatie aan te geven.</span><span class="sxs-lookup"><span data-stu-id="c0077-168">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="c0077-169">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden besproken.</span><span class="sxs-lookup"><span data-stu-id="c0077-169">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="c0077-170">-[Get-item](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="c0077-170">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="c0077-171">Register sleutel waarden weer geven</span><span class="sxs-lookup"><span data-stu-id="c0077-171">Viewing registry key values</span></span>

<span data-ttu-id="c0077-172">Register sleutel waarden worden opgeslagen als eigenschappen van elke register sleutel.</span><span class="sxs-lookup"><span data-stu-id="c0077-172">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="c0077-173">De `Get-ItemProperty` cmdlet bekijkt de register sleutel eigenschappen met de naam die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c0077-173">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="c0077-174">Het resultaat is een **PSCustomObject** die de door u opgegeven eigenschappen bevat.</span><span class="sxs-lookup"><span data-stu-id="c0077-174">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="c0077-175">In het volgende voor beeld wordt de `Get-ItemProperty` cmdlet gebruikt om alle eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c0077-175">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="c0077-176">Als u het resulterende object opslaat in een variabele, kunt u toegang krijgen tot de gewenste eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="c0077-176">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="c0077-177">Door een waarde voor de `-Name` para meter op te geven, selecteert u de eigenschappen die u opgeeft en retourneert de **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="c0077-177">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="c0077-178">In het volgende voor beeld wordt het verschil in uitvoer weer gegeven wanneer u de `-Name` para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0077-178">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="c0077-179">Vanaf Power shell 5,0 retourneert de `Get-ItemPropertyValue` cmdlet alleen de waarde van de eigenschap die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c0077-179">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="c0077-180">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0077-180">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c0077-181">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-181">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="c0077-182">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="c0077-182">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="c0077-183">Register sleutel waarden wijzigen</span><span class="sxs-lookup"><span data-stu-id="c0077-183">Changing registry key values</span></span>

<span data-ttu-id="c0077-184">Met de `Set-ItemProperty` cmdlet worden kenmerken voor register sleutels ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c0077-184">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="c0077-185">In het volgende voor beeld wordt `Set-ItemProperty` het start type van de Spooler-service gewijzigd in hand matig.</span><span class="sxs-lookup"><span data-stu-id="c0077-185">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="c0077-186">In het voor beeld wordt de **starttype** weer gewijzigd in *automatisch* met behulp van de `Set-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0077-186">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="c0077-187">Elke register sleutel heeft een *standaard* waarde.</span><span class="sxs-lookup"><span data-stu-id="c0077-187">Each registry key has a *default* value.</span></span> <span data-ttu-id="c0077-188">U kunt de *standaard* waarde voor een register sleutel wijzigen met ofwel `Set-Item` of `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c0077-188">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="c0077-189">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0077-189">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c0077-190">Set-item</span><span class="sxs-lookup"><span data-stu-id="c0077-190">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="c0077-191">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-191">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="c0077-192">Register sleutels en-waarden maken</span><span class="sxs-lookup"><span data-stu-id="c0077-192">Creating registry keys and values</span></span>

<span data-ttu-id="c0077-193">`New-Item`Met de cmdlet worden register sleutels gemaakt met een naam die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c0077-193">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="c0077-194">U kunt ook de `mkdir` functie gebruiken, die de `New-Item` cmdlet intern aanroept.</span><span class="sxs-lookup"><span data-stu-id="c0077-194">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="c0077-195">U kunt de `New-ItemProperty` cmdlet gebruiken om waarden te maken in een register sleutel die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c0077-195">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="c0077-196">In het volgende voor beeld wordt een nieuwe DWORD-waarde gemaakt voor de register sleutel ContosoCompany.</span><span class="sxs-lookup"><span data-stu-id="c0077-196">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="c0077-197">Raadpleeg de sectie dynamische para meters in dit artikel voor andere toegestane type waarden.</span><span class="sxs-lookup"><span data-stu-id="c0077-197">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="c0077-198">Zie [New-item Property](xref:Microsoft.PowerShell.Management.New-ItemProperty)voor gedetailleerd gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0077-198">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="c0077-199">Register sleutels en-waarden kopiëren</span><span class="sxs-lookup"><span data-stu-id="c0077-199">Copying registry keys and values</span></span>

<span data-ttu-id="c0077-200">Gebruik in de **register** provider de- `Copy-Item` cmdlet om register sleutels en-waarden te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c0077-200">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="c0077-201">Gebruik de `Copy-ItemProperty` cmdlet alleen om register waarden te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c0077-201">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="c0077-202">Met de volgende opdracht worden de register sleutel ' Contoso ' en de bijbehorende eigenschappen gekopieerd naar de opgegeven locatie ' HKLM: \ Software\Fabrikam '.</span><span class="sxs-lookup"><span data-stu-id="c0077-202">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="c0077-203">`Copy-Item` maakt de doel sleutel als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="c0077-203">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="c0077-204">Als de doel sleutel bestaat, `Copy-Item` wordt er een duplicaat van de bron sleutel gemaakt als een onderliggend item (subsleutel) van de doel sleutel.</span><span class="sxs-lookup"><span data-stu-id="c0077-204">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="c0077-205">De volgende opdracht maakt gebruik `Copy-ItemProperty` van de-cmdlet om de waarde ' server ' van de sleutel ' Contoso ' naar de sleutel ' fabrikam ' te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c0077-205">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="c0077-206">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0077-206">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c0077-207">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="c0077-207">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="c0077-208">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-208">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="c0077-209">Register sleutels en-waarden verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c0077-209">Moving registry keys and values</span></span>

<span data-ttu-id="c0077-210">De `Move-Item` `Move-ItemProperty` cmdlets en gedragen zich als hun "kopie"-equivalenten.</span><span class="sxs-lookup"><span data-stu-id="c0077-210">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="c0077-211">Als het doel bestaat, `Move-Item` verplaatst de bron sleutel onder de doel sleutel.</span><span class="sxs-lookup"><span data-stu-id="c0077-211">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="c0077-212">Als de doel sleutel niet bestaat, wordt de bron sleutel verplaatst naar het doelpad.</span><span class="sxs-lookup"><span data-stu-id="c0077-212">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="c0077-213">Met de volgende opdracht wordt de sleutel ' Contoso ' verplaatst naar het pad ' HKLM: \ SOFTWARE\Fabrikam '.</span><span class="sxs-lookup"><span data-stu-id="c0077-213">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="c0077-214">Met deze opdracht worden alle eigenschappen van ' HKLM: \ SOFTWARE\ContosoCompany ' naar ' HKLM: \ SOFTWARE\Fabrikam ' verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c0077-214">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="c0077-215">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0077-215">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c0077-216">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c0077-216">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="c0077-217">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-217">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="c0077-218">De naam van register sleutels en-waarden wijzigen</span><span class="sxs-lookup"><span data-stu-id="c0077-218">Renaming registry keys and values</span></span>

<span data-ttu-id="c0077-219">U kunt de naam van register sleutels en-waarden wijzigen, net zoals u bestanden en mappen zou doen.</span><span class="sxs-lookup"><span data-stu-id="c0077-219">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="c0077-220">`Rename-Item` de naam van register sleutels wijzigen terwijl de naam van de `Rename-ItemProperty` register waarden wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c0077-220">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="c0077-221">Security descriptors wijzigen</span><span class="sxs-lookup"><span data-stu-id="c0077-221">Changing security descriptors</span></span>

<span data-ttu-id="c0077-222">U kunt de toegang tot register sleutels beperken met behulp van de- `Get-Acl` en- `Set-Acl` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c0077-222">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="c0077-223">In het volgende voor beeld wordt een nieuwe gebruiker met volledig beheer toegevoegd aan de register sleutel HKLM: \ SOFTWARE\Contoso.</span><span class="sxs-lookup"><span data-stu-id="c0077-223">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="c0077-224">Raadpleeg de volgende artikelen voor meer voor beelden en Details over het gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0077-224">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="c0077-225">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="c0077-225">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="c0077-226">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="c0077-226">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="c0077-227">Register sleutels en-waarden verwijderen en wissen</span><span class="sxs-lookup"><span data-stu-id="c0077-227">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="c0077-228">U kunt opgenomen items verwijderen met behulp van **Remove-item** , maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="c0077-228">You can remove contained items by using **Remove-Item** , but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="c0077-229">In het volgende voor beeld wordt geprobeerd een sleutel ' HKLM: \ SOFTWARE\Contoso ' te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c0077-229">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="c0077-230">Als u opgenomen items zonder vragen wilt verwijderen, geeft u de `-Recurse` para meter op.</span><span class="sxs-lookup"><span data-stu-id="c0077-230">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="c0077-231">Als u alle items in ' HKLM: \ SOFTWARE\Contoso ' wilt verwijderen, maar niet ' HKLM: \ SOFTWARE\Contoso ' zelf, gebruikt u een afsluitende back slash `\` gevolgd door een Joker teken.</span><span class="sxs-lookup"><span data-stu-id="c0077-231">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="c0077-232">Met deze opdracht wordt de register waarde ' ContosoTest ' verwijderd uit de register sleutel ' HKLM: \ SOFTWARE\Contoso '.</span><span class="sxs-lookup"><span data-stu-id="c0077-232">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="c0077-233">`Clear-Item` Hiermee wist u alle register waarden voor een sleutel.</span><span class="sxs-lookup"><span data-stu-id="c0077-233">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="c0077-234">In het volgende voor beeld worden alle waarden uit de register sleutel HKLM: \ SOFTWARE\Contoso gewist.</span><span class="sxs-lookup"><span data-stu-id="c0077-234">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="c0077-235">Als u alleen een bepaalde eigenschap wilt wissen, gebruikt u `Clear-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c0077-235">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="c0077-236">Raadpleeg de volgende artikelen voor meer voor beelden en Details over het gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0077-236">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="c0077-237">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="c0077-237">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="c0077-238">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-238">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="c0077-239">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="c0077-239">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="c0077-240">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-240">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="c0077-241">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="c0077-241">Dynamic parameters</span></span>

<span data-ttu-id="c0077-242">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="c0077-242">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="c0077-243">Typ <Microsoft. Win32. RegistryValueKind></span><span class="sxs-lookup"><span data-stu-id="c0077-243">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="c0077-244">Hiermee wordt het gegevens type van een register waarde gemaakt of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c0077-244">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="c0077-245">De standaard waarde is `String` (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="c0077-245">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="c0077-246">Deze para meter werkt zoals ontworpen op de cmdlet [set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty) .</span><span class="sxs-lookup"><span data-stu-id="c0077-246">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="c0077-247">Het is ook beschikbaar voor de cmdlet [set-item](xref:Microsoft.PowerShell.Management.Set-Item) in de register stations, maar heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="c0077-247">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="c0077-248">Waarde</span><span class="sxs-lookup"><span data-stu-id="c0077-248">Value</span></span> | <span data-ttu-id="c0077-249">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0077-249">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="c0077-250">Hiermee geeft u een teken reeks met een null-waarde op.</span><span class="sxs-lookup"><span data-stu-id="c0077-250">Specifies a null-terminated string.</span></span> <span data-ttu-id="c0077-251">Gelijk aan REG_SZ.</span><span class="sxs-lookup"><span data-stu-id="c0077-251">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="c0077-252">Hiermee wordt een teken reeks met een null-waarde beëindigd die niet is uitgevouwen</span><span class="sxs-lookup"><span data-stu-id="c0077-252">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="c0077-253">verwijzingen naar omgevings variabelen die worden uitgebreid wanneer</span><span class="sxs-lookup"><span data-stu-id="c0077-253">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="c0077-254">de waarde wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c0077-254">the value is retrieved.</span></span> <span data-ttu-id="c0077-255">Gelijk aan REG_EXPAND_SZ.</span><span class="sxs-lookup"><span data-stu-id="c0077-255">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="c0077-256">Hiermee worden binaire gegevens in een formulier opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c0077-256">Specifies binary data in any form.</span></span> <span data-ttu-id="c0077-257">Gelijk aan REG_BINARY.</span><span class="sxs-lookup"><span data-stu-id="c0077-257">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="c0077-258">Hiermee geeft u een 32-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="c0077-258">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="c0077-259">Gelijk aan REG_DWORD.</span><span class="sxs-lookup"><span data-stu-id="c0077-259">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="c0077-260">Hiermee geeft u een matrix van op null eindigende teken reeksen die zijn beëindigd door</span><span class="sxs-lookup"><span data-stu-id="c0077-260">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="c0077-261">twee null-tekens.</span><span class="sxs-lookup"><span data-stu-id="c0077-261">two null characters.</span></span> <span data-ttu-id="c0077-262">Gelijk aan REG_MULTI_SZ.</span><span class="sxs-lookup"><span data-stu-id="c0077-262">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="c0077-263">Hiermee geeft u een 64-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="c0077-263">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="c0077-264">Gelijk aan REG_QWORD.</span><span class="sxs-lookup"><span data-stu-id="c0077-264">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="c0077-265">Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals</span><span class="sxs-lookup"><span data-stu-id="c0077-265">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="c0077-266">REG_RESOURCE_LIST.</span><span class="sxs-lookup"><span data-stu-id="c0077-266">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="c0077-267">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="c0077-267">Cmdlets supported</span></span>

- [<span data-ttu-id="c0077-268">Set-item</span><span class="sxs-lookup"><span data-stu-id="c0077-268">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="c0077-269">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c0077-269">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="c0077-270">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="c0077-270">Using the pipeline</span></span>

<span data-ttu-id="c0077-271">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c0077-271">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="c0077-272">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="c0077-272">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="c0077-273">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c0077-273">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="c0077-274">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="c0077-274">Getting help</span></span>

<span data-ttu-id="c0077-275">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="c0077-275">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="c0077-276">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u een `Get-Help` opdracht uit in een bestandssysteem station of gebruikt u de para meter **Path** om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="c0077-276">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="c0077-277">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c0077-277">See also</span></span>

 [<span data-ttu-id="c0077-278">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c0077-278">about_Providers</span></span>](../About/about_Providers.md)
