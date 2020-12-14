---
description: Register
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register provider
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705329"
---
# <a name="registry-provider"></a><span data-ttu-id="c74b1-103">Register provider</span><span class="sxs-lookup"><span data-stu-id="c74b1-103">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="c74b1-104">Provider naam</span><span class="sxs-lookup"><span data-stu-id="c74b1-104">Provider name</span></span>

<span data-ttu-id="c74b1-105">Register</span><span class="sxs-lookup"><span data-stu-id="c74b1-105">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="c74b1-106">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="c74b1-106">Drives</span></span>

<span data-ttu-id="c74b1-107">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="c74b1-107">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="c74b1-108">Functies</span><span class="sxs-lookup"><span data-stu-id="c74b1-108">Capabilities</span></span>

<span data-ttu-id="c74b1-109">**ShouldProcess**, **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="c74b1-109">**ShouldProcess**, **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="c74b1-110">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="c74b1-110">Short description</span></span>

<span data-ttu-id="c74b1-111">Biedt toegang tot de register sleutels, vermeldingen en waarden in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c74b1-111">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="c74b1-112">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="c74b1-112">Detailed description</span></span>

<span data-ttu-id="c74b1-113">Met de Power shell- **register** provider kunt u register sleutels, vermeldingen en waarden in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c74b1-113">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="c74b1-114">De **register** stations zijn een hiërarchische naam ruimte met de register sleutels en subsleutels op uw computer.</span><span class="sxs-lookup"><span data-stu-id="c74b1-114">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="c74b1-115">Register vermeldingen en-waarden zijn geen onderdelen van die hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="c74b1-115">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="c74b1-116">In plaats daarvan zijn ze eigenschappen van elk van de sleutels.</span><span class="sxs-lookup"><span data-stu-id="c74b1-116">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="c74b1-117">De **register** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="c74b1-117">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="c74b1-118">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="c74b1-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="c74b1-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="c74b1-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="c74b1-120">Get-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="c74b1-121">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="c74b1-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="c74b1-122">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="c74b1-123">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c74b1-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="c74b1-124">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="c74b1-125">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="c74b1-126">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="c74b1-127">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="c74b1-128">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-128">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="c74b1-129">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="c74b1-130">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="c74b1-130">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="c74b1-131">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="c74b1-131">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="c74b1-132">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="c74b1-132">Types exposed by this provider</span></span>

<span data-ttu-id="c74b1-133">Register sleutels worden weer gegeven als exemplaren van de klasse [micro soft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) .</span><span class="sxs-lookup"><span data-stu-id="c74b1-133">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="c74b1-134">Register vermeldingen worden weer gegeven als exemplaren van de klasse [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .</span><span class="sxs-lookup"><span data-stu-id="c74b1-134">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="c74b1-135">Navigeren door de register stations</span><span class="sxs-lookup"><span data-stu-id="c74b1-135">Navigating the Registry drives</span></span>

<span data-ttu-id="c74b1-136">De gegevens opslag van de **register** provider is beschikbaar als twee standaard stations.</span><span class="sxs-lookup"><span data-stu-id="c74b1-136">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="c74b1-137">De register locatie HKEY_LOCAL_MACHINE wordt toegewezen aan het `HKLM:` station en HKEY_CURRENT_USER wordt toegewezen aan het `HKCU:` station.</span><span class="sxs-lookup"><span data-stu-id="c74b1-137">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="c74b1-138">Als u wilt werken met het REGI ster, kunt u uw locatie wijzigen in het `HKLM:` station met behulp van de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="c74b1-138">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="c74b1-139">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="c74b1-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="c74b1-140">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c74b1-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="c74b1-141">U kunt ook met de **register** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="c74b1-141">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="c74b1-142">Als u wilt verwijzen naar een register sleutel van een andere locatie, gebruikt u de naam van het station ( `HKLM:` , `HKCU:` ) in het pad.</span><span class="sxs-lookup"><span data-stu-id="c74b1-142">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="c74b1-143">Gebruik een back slash ( \\ ) of een slash (/) om een niveau van het **register** station aan te geven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-143">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="c74b1-144">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="c74b1-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="c74b1-145">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="c74b1-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="c74b1-146">Dit laatste voor beeld toont een andere pad-syntaxis die u kunt gebruiken om te navigeren door de **register** provider.</span><span class="sxs-lookup"><span data-stu-id="c74b1-146">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="c74b1-147">Deze syntaxis maakt gebruik van de provider naam, gevolgd door twee dubbele punten `::` .</span><span class="sxs-lookup"><span data-stu-id="c74b1-147">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="c74b1-148">Met deze syntaxis kunt u de volledige HIVE-naam gebruiken in plaats van de naam van het toegewezen station `HKLM` .</span><span class="sxs-lookup"><span data-stu-id="c74b1-148">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="c74b1-149">De inhoud van register sleutels weer geven</span><span class="sxs-lookup"><span data-stu-id="c74b1-149">Displaying the contents of registry keys</span></span>

<span data-ttu-id="c74b1-150">Het REGI ster is onderverdeeld in sleutels, subsleutels en vermeldingen.</span><span class="sxs-lookup"><span data-stu-id="c74b1-150">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="c74b1-151">Zie [structuur van het REGI ster](/windows/desktop/sysinfo/structure-of-the-registry)voor meer informatie over de Register structuur.</span><span class="sxs-lookup"><span data-stu-id="c74b1-151">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="c74b1-152">In een **register** station is elke sleutel een container.</span><span class="sxs-lookup"><span data-stu-id="c74b1-152">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="c74b1-153">Een sleutel kan een wille keurig aantal sleutels bevatten.</span><span class="sxs-lookup"><span data-stu-id="c74b1-153">A key can contain any number of keys.</span></span> <span data-ttu-id="c74b1-154">Een register sleutel met een bovenliggende sleutel wordt een subsleutel genoemd.</span><span class="sxs-lookup"><span data-stu-id="c74b1-154">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="c74b1-155">U kunt gebruiken `Get-ChildItem` om register sleutels weer te geven en naar `Set-Location` een sleutelpad te navigeren.</span><span class="sxs-lookup"><span data-stu-id="c74b1-155">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="c74b1-156">Register waarden zijn kenmerken van een register sleutel.</span><span class="sxs-lookup"><span data-stu-id="c74b1-156">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="c74b1-157">In het **register** station worden deze **item eigenschappen** genoemd.</span><span class="sxs-lookup"><span data-stu-id="c74b1-157">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="c74b1-158">Een register sleutel kan zowel onderliggende sleutels als item eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="c74b1-158">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="c74b1-159">In dit voor beeld wordt het verschil tussen `Get-Item` en `Get-ChildItem` weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-159">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="c74b1-160">Wanneer u `Get-Item` op de register sleutel ' spooler ' gebruikt, kunt u de eigenschappen ervan weer geven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-160">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

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

<span data-ttu-id="c74b1-161">Elke register sleutel kan ook subsleutels hebben.</span><span class="sxs-lookup"><span data-stu-id="c74b1-161">Each registry key can also have subkeys.</span></span> <span data-ttu-id="c74b1-162">Wanneer u `Get-Item` een register sleutel gebruikt, worden de subsleutels niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-162">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="c74b1-163">`Get-ChildItem`Met de cmdlet worden de onderliggende items van de ' spooler-sleutel ' weer gegeven, inclusief de eigenschappen van elke subsleutel.</span><span class="sxs-lookup"><span data-stu-id="c74b1-163">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="c74b1-164">De eigenschappen van de bovenliggende sleutels worden niet weer gegeven wanneer u gebruikt `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="c74b1-164">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

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

<span data-ttu-id="c74b1-165">De `Get-Item` cmdlet kan ook worden gebruikt op de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="c74b1-165">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="c74b1-166">In het volgende voor beeld wordt naar de register sleutel ' spooler ' genavigeerd en worden de item eigenschappen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c74b1-166">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="c74b1-167">De punt `.` wordt gebruikt om de huidige locatie aan te geven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-167">The dot `.` is used to indicate the current location.</span></span>

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

<span data-ttu-id="c74b1-168">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden besproken.</span><span class="sxs-lookup"><span data-stu-id="c74b1-168">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="c74b1-169">-[Get-item](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="c74b1-169">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="c74b1-170">Register sleutel waarden weer geven</span><span class="sxs-lookup"><span data-stu-id="c74b1-170">Viewing registry key values</span></span>

<span data-ttu-id="c74b1-171">Register sleutel waarden worden opgeslagen als eigenschappen van elke register sleutel.</span><span class="sxs-lookup"><span data-stu-id="c74b1-171">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="c74b1-172">De `Get-ItemProperty` cmdlet bekijkt de register sleutel eigenschappen met de naam die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c74b1-172">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="c74b1-173">Het resultaat is een **PSCustomObject** die de door u opgegeven eigenschappen bevat.</span><span class="sxs-lookup"><span data-stu-id="c74b1-173">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="c74b1-174">In het volgende voor beeld wordt de `Get-ItemProperty` cmdlet gebruikt om alle eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-174">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="c74b1-175">Als u het resulterende object opslaat in een variabele, kunt u toegang krijgen tot de gewenste eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="c74b1-175">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="c74b1-176">Door een waarde voor de `-Name` para meter op te geven, selecteert u de eigenschappen die u opgeeft en retourneert de **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="c74b1-176">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="c74b1-177">In het volgende voor beeld wordt het verschil in uitvoer weer gegeven wanneer u de `-Name` para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c74b1-177">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

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

<span data-ttu-id="c74b1-178">Vanaf Power shell 5,0 retourneert de `Get-ItemPropertyValue` cmdlet alleen de waarde van de eigenschap die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c74b1-178">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="c74b1-179">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c74b1-179">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c74b1-180">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-180">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="c74b1-181">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="c74b1-181">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="c74b1-182">Register sleutel waarden wijzigen</span><span class="sxs-lookup"><span data-stu-id="c74b1-182">Changing registry key values</span></span>

<span data-ttu-id="c74b1-183">Met de `Set-ItemProperty` cmdlet worden kenmerken voor register sleutels ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c74b1-183">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="c74b1-184">In het volgende voor beeld wordt `Set-ItemProperty` het start type van de Spooler-service gewijzigd in hand matig.</span><span class="sxs-lookup"><span data-stu-id="c74b1-184">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="c74b1-185">In het voor beeld wordt de **starttype** weer gewijzigd in *automatisch* met behulp van de `Set-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c74b1-185">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

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

<span data-ttu-id="c74b1-186">Elke register sleutel heeft een *standaard* waarde.</span><span class="sxs-lookup"><span data-stu-id="c74b1-186">Each registry key has a *default* value.</span></span> <span data-ttu-id="c74b1-187">U kunt de *standaard* waarde voor een register sleutel wijzigen met ofwel `Set-Item` of `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c74b1-187">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="c74b1-188">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c74b1-188">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c74b1-189">Set-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-189">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="c74b1-190">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-190">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="c74b1-191">Register sleutels en-waarden maken</span><span class="sxs-lookup"><span data-stu-id="c74b1-191">Creating registry keys and values</span></span>

<span data-ttu-id="c74b1-192">`New-Item`Met de cmdlet worden register sleutels gemaakt met een naam die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c74b1-192">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="c74b1-193">U kunt ook de `mkdir` functie gebruiken, die de `New-Item` cmdlet intern aanroept.</span><span class="sxs-lookup"><span data-stu-id="c74b1-193">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="c74b1-194">U kunt de `New-ItemProperty` cmdlet gebruiken om waarden te maken in een register sleutel die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c74b1-194">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="c74b1-195">In het volgende voor beeld wordt een nieuwe DWORD-waarde gemaakt voor de register sleutel ContosoCompany.</span><span class="sxs-lookup"><span data-stu-id="c74b1-195">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="c74b1-196">Raadpleeg de sectie dynamische para meters in dit artikel voor andere toegestane type waarden.</span><span class="sxs-lookup"><span data-stu-id="c74b1-196">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="c74b1-197">Zie [New-item Property](xref:Microsoft.PowerShell.Management.New-ItemProperty)voor gedetailleerd gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c74b1-197">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="c74b1-198">Register sleutels en-waarden kopiëren</span><span class="sxs-lookup"><span data-stu-id="c74b1-198">Copying registry keys and values</span></span>

<span data-ttu-id="c74b1-199">Gebruik in de **register** provider de- `Copy-Item` cmdlet om register sleutels en-waarden te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c74b1-199">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="c74b1-200">Gebruik de `Copy-ItemProperty` cmdlet alleen om register waarden te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c74b1-200">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="c74b1-201">Met de volgende opdracht worden de register sleutel ' Contoso ' en de bijbehorende eigenschappen gekopieerd naar de opgegeven locatie ' HKLM: \ Software\Fabrikam '.</span><span class="sxs-lookup"><span data-stu-id="c74b1-201">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="c74b1-202">`Copy-Item` maakt de doel sleutel als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="c74b1-202">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="c74b1-203">Als de doel sleutel bestaat, `Copy-Item` wordt er een duplicaat van de bron sleutel gemaakt als een onderliggend item (subsleutel) van de doel sleutel.</span><span class="sxs-lookup"><span data-stu-id="c74b1-203">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="c74b1-204">De volgende opdracht maakt gebruik `Copy-ItemProperty` van de-cmdlet om de waarde ' server ' van de sleutel ' Contoso ' naar de sleutel ' fabrikam ' te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c74b1-204">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="c74b1-205">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c74b1-205">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c74b1-206">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-206">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="c74b1-207">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-207">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="c74b1-208">Register sleutels en-waarden verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c74b1-208">Moving registry keys and values</span></span>

<span data-ttu-id="c74b1-209">De `Move-Item` `Move-ItemProperty` cmdlets en gedragen zich als hun "kopie"-equivalenten.</span><span class="sxs-lookup"><span data-stu-id="c74b1-209">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="c74b1-210">Als het doel bestaat, `Move-Item` verplaatst de bron sleutel onder de doel sleutel.</span><span class="sxs-lookup"><span data-stu-id="c74b1-210">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="c74b1-211">Als de doel sleutel niet bestaat, wordt de bron sleutel verplaatst naar het doelpad.</span><span class="sxs-lookup"><span data-stu-id="c74b1-211">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="c74b1-212">Met de volgende opdracht wordt de sleutel ' Contoso ' verplaatst naar het pad ' HKLM: \ SOFTWARE\Fabrikam '.</span><span class="sxs-lookup"><span data-stu-id="c74b1-212">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="c74b1-213">Met deze opdracht worden alle eigenschappen van ' HKLM: \ SOFTWARE\ContosoCompany ' naar ' HKLM: \ SOFTWARE\Fabrikam ' verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c74b1-213">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="c74b1-214">Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c74b1-214">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c74b1-215">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c74b1-215">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="c74b1-216">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-216">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="c74b1-217">De naam van register sleutels en-waarden wijzigen</span><span class="sxs-lookup"><span data-stu-id="c74b1-217">Renaming registry keys and values</span></span>

<span data-ttu-id="c74b1-218">U kunt de naam van register sleutels en-waarden wijzigen, net zoals u bestanden en mappen zou doen.</span><span class="sxs-lookup"><span data-stu-id="c74b1-218">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="c74b1-219">`Rename-Item` de naam van register sleutels wijzigen terwijl de naam van de `Rename-ItemProperty` register waarden wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c74b1-219">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="c74b1-220">Security descriptors wijzigen</span><span class="sxs-lookup"><span data-stu-id="c74b1-220">Changing security descriptors</span></span>

<span data-ttu-id="c74b1-221">U kunt de toegang tot register sleutels beperken met behulp van de- `Get-Acl` en- `Set-Acl` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c74b1-221">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="c74b1-222">In het volgende voor beeld wordt een nieuwe gebruiker met volledig beheer toegevoegd aan de register sleutel HKLM: \ SOFTWARE\Contoso.</span><span class="sxs-lookup"><span data-stu-id="c74b1-222">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="c74b1-223">Raadpleeg de volgende artikelen voor meer voor beelden en Details over het gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c74b1-223">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="c74b1-224">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="c74b1-224">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="c74b1-225">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="c74b1-225">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="c74b1-226">Register sleutels en-waarden verwijderen en wissen</span><span class="sxs-lookup"><span data-stu-id="c74b1-226">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="c74b1-227">U kunt opgenomen items verwijderen met behulp van **Remove-item**, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="c74b1-227">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="c74b1-228">In het volgende voor beeld wordt geprobeerd een sleutel ' HKLM: \ SOFTWARE\Contoso ' te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c74b1-228">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

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

<span data-ttu-id="c74b1-229">Als u opgenomen items zonder vragen wilt verwijderen, geeft u de `-Recurse` para meter op.</span><span class="sxs-lookup"><span data-stu-id="c74b1-229">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="c74b1-230">Als u alle items in ' HKLM: \ SOFTWARE\Contoso ' wilt verwijderen, maar niet ' HKLM: \ SOFTWARE\Contoso ' zelf, gebruikt u een afsluitende back slash `\` gevolgd door een Joker teken.</span><span class="sxs-lookup"><span data-stu-id="c74b1-230">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="c74b1-231">Met deze opdracht wordt de register waarde ' ContosoTest ' verwijderd uit de register sleutel ' HKLM: \ SOFTWARE\Contoso '.</span><span class="sxs-lookup"><span data-stu-id="c74b1-231">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="c74b1-232">`Clear-Item` Hiermee wist u alle register waarden voor een sleutel.</span><span class="sxs-lookup"><span data-stu-id="c74b1-232">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="c74b1-233">In het volgende voor beeld worden alle waarden uit de register sleutel HKLM: \ SOFTWARE\Contoso gewist.</span><span class="sxs-lookup"><span data-stu-id="c74b1-233">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="c74b1-234">Als u alleen een bepaalde eigenschap wilt wissen, gebruikt u `Clear-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c74b1-234">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

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

<span data-ttu-id="c74b1-235">Raadpleeg de volgende artikelen voor meer voor beelden en Details over het gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c74b1-235">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="c74b1-236">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-236">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="c74b1-237">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-237">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="c74b1-238">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-238">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="c74b1-239">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-239">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="c74b1-240">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="c74b1-240">Dynamic parameters</span></span>

<span data-ttu-id="c74b1-241">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="c74b1-241">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="c74b1-242">Typ <Microsoft. Win32. RegistryValueKind></span><span class="sxs-lookup"><span data-stu-id="c74b1-242">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="c74b1-243">Hiermee wordt het gegevens type van een register waarde gemaakt of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c74b1-243">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="c74b1-244">De standaard waarde is `String` (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="c74b1-244">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="c74b1-245">Deze para meter werkt zoals ontworpen op de cmdlet [set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty) .</span><span class="sxs-lookup"><span data-stu-id="c74b1-245">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="c74b1-246">Het is ook beschikbaar voor de cmdlet [set-item](xref:Microsoft.PowerShell.Management.Set-Item) in de register stations, maar heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="c74b1-246">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="c74b1-247">Waarde</span><span class="sxs-lookup"><span data-stu-id="c74b1-247">Value</span></span> | <span data-ttu-id="c74b1-248">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c74b1-248">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="c74b1-249">Hiermee geeft u een teken reeks met een null-waarde op.</span><span class="sxs-lookup"><span data-stu-id="c74b1-249">Specifies a null-terminated string.</span></span> <span data-ttu-id="c74b1-250">Gelijk aan REG_SZ.</span><span class="sxs-lookup"><span data-stu-id="c74b1-250">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="c74b1-251">Hiermee wordt een teken reeks met een null-waarde beëindigd die niet is uitgevouwen</span><span class="sxs-lookup"><span data-stu-id="c74b1-251">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="c74b1-252">verwijzingen naar omgevings variabelen die worden uitgebreid wanneer</span><span class="sxs-lookup"><span data-stu-id="c74b1-252">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="c74b1-253">de waarde wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c74b1-253">the value is retrieved.</span></span> <span data-ttu-id="c74b1-254">Gelijk aan REG_EXPAND_SZ.</span><span class="sxs-lookup"><span data-stu-id="c74b1-254">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="c74b1-255">Hiermee worden binaire gegevens in een formulier opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-255">Specifies binary data in any form.</span></span> <span data-ttu-id="c74b1-256">Gelijk aan REG_BINARY.</span><span class="sxs-lookup"><span data-stu-id="c74b1-256">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="c74b1-257">Hiermee geeft u een 32-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="c74b1-257">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="c74b1-258">Gelijk aan REG_DWORD.</span><span class="sxs-lookup"><span data-stu-id="c74b1-258">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="c74b1-259">Hiermee geeft u een matrix van op null eindigende teken reeksen die zijn beëindigd door</span><span class="sxs-lookup"><span data-stu-id="c74b1-259">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="c74b1-260">twee null-tekens.</span><span class="sxs-lookup"><span data-stu-id="c74b1-260">two null characters.</span></span> <span data-ttu-id="c74b1-261">Gelijk aan REG_MULTI_SZ.</span><span class="sxs-lookup"><span data-stu-id="c74b1-261">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="c74b1-262">Hiermee geeft u een 64-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="c74b1-262">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="c74b1-263">Gelijk aan REG_QWORD.</span><span class="sxs-lookup"><span data-stu-id="c74b1-263">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="c74b1-264">Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals</span><span class="sxs-lookup"><span data-stu-id="c74b1-264">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="c74b1-265">REG_RESOURCE_LIST.</span><span class="sxs-lookup"><span data-stu-id="c74b1-265">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="c74b1-266">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="c74b1-266">Cmdlets supported</span></span>

- [<span data-ttu-id="c74b1-267">Set-item</span><span class="sxs-lookup"><span data-stu-id="c74b1-267">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="c74b1-268">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c74b1-268">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="c74b1-269">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="c74b1-269">Using the pipeline</span></span>

<span data-ttu-id="c74b1-270">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c74b1-270">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="c74b1-271">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="c74b1-271">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="c74b1-272">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c74b1-272">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="c74b1-273">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="c74b1-273">Getting help</span></span>

<span data-ttu-id="c74b1-274">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="c74b1-274">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="c74b1-275">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u een `Get-Help` opdracht uit in een bestandssysteem station of gebruikt u de para meter **Path** om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="c74b1-275">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="c74b1-276">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c74b1-276">See also</span></span>

 [<span data-ttu-id="c74b1-277">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c74b1-277">about_Providers</span></span>](../About/about_Providers.md)

