---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Alias provider
ms.openlocfilehash: e5251b6e36da5e5c32d9e7c826766aa3dc38a9e0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252388"
---
# <a name="alias-provider"></a><span data-ttu-id="05b71-104">Alias provider</span><span class="sxs-lookup"><span data-stu-id="05b71-104">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="05b71-105">Provider naam</span><span class="sxs-lookup"><span data-stu-id="05b71-105">Provider name</span></span>
<span data-ttu-id="05b71-106">Alias</span><span class="sxs-lookup"><span data-stu-id="05b71-106">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="05b71-107">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="05b71-107">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="05b71-108">Functies</span><span class="sxs-lookup"><span data-stu-id="05b71-108">Capabilities</span></span>

<span data-ttu-id="05b71-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="05b71-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="05b71-110">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="05b71-110">Short description</span></span>

<span data-ttu-id="05b71-111">Geeft toegang tot de Power shell-aliassen en de waarden die ze vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="05b71-111">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="05b71-112">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="05b71-112">Detailed description</span></span>

<span data-ttu-id="05b71-113">Met de Power shell- **alias** provider kunt u aliassen ophalen, toevoegen, wijzigen, wissen en verwijderen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="05b71-113">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="05b71-114">Een alias is een alternatieve naam voor een cmdlet, functie, uitvoerbaar bestand, met inbegrip van scripts.</span><span class="sxs-lookup"><span data-stu-id="05b71-114">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="05b71-115">Power shell bevat een reeks ingebouwde aliassen.</span><span class="sxs-lookup"><span data-stu-id="05b71-115">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="05b71-116">U kunt uw eigen aliassen toevoegen aan de huidige sessie en aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="05b71-116">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="05b71-117">Het **alias** station is een platte naam ruimte die alleen de alias-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="05b71-117">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="05b71-118">De aliassen hebben geen onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="05b71-118">The aliases have no child items.</span></span>

<span data-ttu-id="05b71-119">De **alias** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="05b71-119">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="05b71-120">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="05b71-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="05b71-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="05b71-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="05b71-122">Get-item</span><span class="sxs-lookup"><span data-stu-id="05b71-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="05b71-123">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="05b71-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="05b71-124">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="05b71-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="05b71-125">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="05b71-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="05b71-126">Power shell bevat een set cmdlets die zijn ontworpen om aliassen weer te geven en te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="05b71-126">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="05b71-127">Wanneer u **alias** -cmdlets gebruikt, hoeft u het `Alias:` station niet in de naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="05b71-127">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="05b71-128">Dit artikel is niet van belang voor het werken met **alias** -cmdlets.</span><span class="sxs-lookup"><span data-stu-id="05b71-128">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="05b71-129">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="05b71-129">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="05b71-130">Get-alias</span><span class="sxs-lookup"><span data-stu-id="05b71-130">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="05b71-131">Import-alias</span><span class="sxs-lookup"><span data-stu-id="05b71-131">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="05b71-132">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="05b71-132">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="05b71-133">Set-alias</span><span class="sxs-lookup"><span data-stu-id="05b71-133">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="05b71-134">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="05b71-134">Types exposed by this provider</span></span>

<span data-ttu-id="05b71-135">Elke alias is een instantie van de klasse [System. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .</span><span class="sxs-lookup"><span data-stu-id="05b71-135">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="05b71-136">Navigeren door het alias station</span><span class="sxs-lookup"><span data-stu-id="05b71-136">Navigating the Alias drive</span></span>

<span data-ttu-id="05b71-137">De **alias** provider toont het gegevens archief van het `Alias:` station.</span><span class="sxs-lookup"><span data-stu-id="05b71-137">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="05b71-138">Als u met aliassen wilt werken, kunt u uw locatie wijzigen in het `Alias:` station met behulp van de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="05b71-138">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="05b71-139">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="05b71-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="05b71-140">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="05b71-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="05b71-141">U kunt ook met de alias provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="05b71-141">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="05b71-142">Als u wilt verwijzen naar een alias vanuit een andere locatie, gebruikt u de `Alias:` naam van het station in het pad.</span><span class="sxs-lookup"><span data-stu-id="05b71-142">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="05b71-143">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="05b71-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="05b71-144">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="05b71-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="05b71-145">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="05b71-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="05b71-146">De inhoud van de alias wordt weer gegeven: station</span><span class="sxs-lookup"><span data-stu-id="05b71-146">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="05b71-147">Met deze opdracht wordt de lijst met alle aliassen opgehaald wanneer de huidige locatie het `Alias:` station is.</span><span class="sxs-lookup"><span data-stu-id="05b71-147">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="05b71-148">Er wordt een Joker teken gebruikt `*` om alle inhoud van de huidige locatie aan te geven.</span><span class="sxs-lookup"><span data-stu-id="05b71-148">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="05b71-149">In het `Alias:` station, een punt `.` , dat de huidige locatie vertegenwoordigt en een Joker teken `*` , waarmee alle items op de huidige locatie worden aangeduid, hebben hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="05b71-149">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="05b71-150">U kunt bijvoorbeeld `Get-Item -Path .` `Get-Item \*` hetzelfde resultaat opleveren.</span><span class="sxs-lookup"><span data-stu-id="05b71-150">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="05b71-151">De alias provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het wordt gebruikt in combi natie met `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="05b71-151">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="05b71-152">Een geselecteerde alias ophalen</span><span class="sxs-lookup"><span data-stu-id="05b71-152">Get a selected alias</span></span>

<span data-ttu-id="05b71-153">Met deze opdracht wordt de `ls` alias opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05b71-153">This command gets the `ls` alias.</span></span>
<span data-ttu-id="05b71-154">Omdat deze het pad bevat, kunt u het gebruiken in een Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="05b71-154">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="05b71-155">Als u zich in het station bevindt `Alias:` , kunt u de naam van het station weglaten uit het pad.</span><span class="sxs-lookup"><span data-stu-id="05b71-155">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="05b71-156">U kunt ook de definitie voor een alias ophalen door het pad naar de provider te voorzien van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="05b71-156">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="05b71-157">Alle aliassen voor een specifieke cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="05b71-157">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="05b71-158">Met deze opdracht wordt een lijst opgehaald met de aliassen die zijn gekoppeld aan de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05b71-158">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="05b71-159">De eigenschap **definitie** wordt gebruikt om de naam van de cmdlet op te slaan.</span><span class="sxs-lookup"><span data-stu-id="05b71-159">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="05b71-160">Aliassen maken</span><span class="sxs-lookup"><span data-stu-id="05b71-160">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="05b71-161">Een alias maken op basis van de alias: station</span><span class="sxs-lookup"><span data-stu-id="05b71-161">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="05b71-162">Met deze opdracht wordt de `serv` alias voor de `Get-Service` cmdlet gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05b71-162">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="05b71-163">Omdat de huidige locatie zich in het station bevindt `Alias:` , `-Path` is de para meter niet nodig.</span><span class="sxs-lookup"><span data-stu-id="05b71-163">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="05b71-164">Met deze opdracht wordt ook de `-Options` dynamische para meter gebruikt om de **AllScope** -optie in te stellen voor de alias.</span><span class="sxs-lookup"><span data-stu-id="05b71-164">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="05b71-165">De `-Options` para meter is alleen beschikbaar in de `New-Item` cmdlet als u zich in het station bevindt `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="05b71-165">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="05b71-166">De punt ( `.` ) geeft de huidige map aan. Dit is het alias station.</span><span class="sxs-lookup"><span data-stu-id="05b71-166">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="05b71-167">Een alias met een absoluut pad maken</span><span class="sxs-lookup"><span data-stu-id="05b71-167">Create an alias with an absolute path</span></span>

<span data-ttu-id="05b71-168">U kunt een alias maken voor elk item dat een opdracht aanroept.</span><span class="sxs-lookup"><span data-stu-id="05b71-168">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="05b71-169">Met deze opdracht maakt u de `np` alias voor `Notepad.exe` .</span><span class="sxs-lookup"><span data-stu-id="05b71-169">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="05b71-170">Een alias maken voor een nieuwe functie</span><span class="sxs-lookup"><span data-stu-id="05b71-170">Create an alias to a new function</span></span>

<span data-ttu-id="05b71-171">U kunt voor elke functie een alias maken.</span><span class="sxs-lookup"><span data-stu-id="05b71-171">You can create an alias for any function.</span></span> <span data-ttu-id="05b71-172">U kunt deze functie gebruiken om een alias te maken die zowel een cmdlet als de bijbehorende para meters bevat.</span><span class="sxs-lookup"><span data-stu-id="05b71-172">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="05b71-173">Met de eerste opdracht wordt de `CD32` functie gemaakt, waarmee de huidige map wordt gewijzigd in de `System32` map.</span><span class="sxs-lookup"><span data-stu-id="05b71-173">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="05b71-174">Met de tweede opdracht wordt de `go` alias voor de `CD32` functie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05b71-174">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="05b71-175">Wanneer de opdracht is voltooid, kunt u ofwel `CD32` of gebruiken `go` om de functie aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="05b71-175">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="05b71-176">Aliassen wijzigen</span><span class="sxs-lookup"><span data-stu-id="05b71-176">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="05b71-177">De opties van een alias wijzigen</span><span class="sxs-lookup"><span data-stu-id="05b71-177">Change the options of an alias</span></span>

<span data-ttu-id="05b71-178">U kunt de `Set-Item` cmdlet met de `-Options` para meter Dynamic gebruiken om de waarde van de `-Options` eigenschap van een alias te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="05b71-178">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="05b71-179">Met deze opdracht worden de opties **AllScope** en **ReadOnly** ingesteld voor de `dir` alias.</span><span class="sxs-lookup"><span data-stu-id="05b71-179">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="05b71-180">De opdracht maakt gebruik `-Options` van de dynamische para meter van de `Set-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05b71-180">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="05b71-181">De `-Options` para meter is beschikbaar in `Set-Item` Wanneer u deze gebruikt met de **alias** of **functie** provider.</span><span class="sxs-lookup"><span data-stu-id="05b71-181">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="05b71-182">Een alias waarnaar wordt verwezen, wijzigen</span><span class="sxs-lookup"><span data-stu-id="05b71-182">Change an aliases referenced command</span></span>

<span data-ttu-id="05b71-183">Met deze opdracht wordt de- `Set-Item` cmdlet gebruikt om de alias te wijzigen `gp` zodat deze de `Get-Process` cmdlet vertegenwoordigt in plaats van de `Get-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05b71-183">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="05b71-184">De `-Force` para meter is vereist omdat de waarde van de eigenschap **Options** van de `gp` alias is ingesteld op `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="05b71-184">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="05b71-185">Omdat de opdracht vanuit het station wordt verzonden `Alias:` , is het station niet opgegeven in het pad.</span><span class="sxs-lookup"><span data-stu-id="05b71-185">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="05b71-186">De wijziging is van invloed op de vier eigenschappen die de koppeling tussen de alias en de opdracht definiëren.</span><span class="sxs-lookup"><span data-stu-id="05b71-186">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="05b71-187">Als u het effect van de wijziging wilt weer geven, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="05b71-187">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="05b71-188">Naam wijzigen van een alias</span><span class="sxs-lookup"><span data-stu-id="05b71-188">Rename an alias</span></span>

<span data-ttu-id="05b71-189">Met deze opdracht wordt de- `Rename-Item` cmdlet gebruikt om de `popd` alias te wijzigen in `pop` .</span><span class="sxs-lookup"><span data-stu-id="05b71-189">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="05b71-190">Een alias kopiëren</span><span class="sxs-lookup"><span data-stu-id="05b71-190">Copying an alias</span></span>

<span data-ttu-id="05b71-191">Met deze opdracht `pushd` wordt de alias gekopieerd zodat er een nieuwe `push` alias voor de `Push-Location` cmdlet wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05b71-191">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="05b71-192">Wanneer de nieuwe alias wordt gemaakt, heeft de eigenschap **Description** een null-waarde.</span><span class="sxs-lookup"><span data-stu-id="05b71-192">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="05b71-193">En de **optie** eigenschap heeft de waarde `None` .</span><span class="sxs-lookup"><span data-stu-id="05b71-193">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="05b71-194">Als de opdracht wordt verleend vanuit het `Alias:` station, kunt u de naam van het station weglaten uit de waarde van de `-Path` para meter.</span><span class="sxs-lookup"><span data-stu-id="05b71-194">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="05b71-195">Een alias verwijderen</span><span class="sxs-lookup"><span data-stu-id="05b71-195">Deleting an alias</span></span>

<span data-ttu-id="05b71-196">Met deze opdracht wordt de `serv` alias van de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="05b71-196">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="05b71-197">U kunt deze opdracht in elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="05b71-197">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="05b71-198">Met deze opdracht worden aliassen verwijderd die beginnen met s.</span><span class="sxs-lookup"><span data-stu-id="05b71-198">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="05b71-199">Er worden geen alleen-lezen-aliassen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="05b71-199">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="05b71-200">Alleen-lezen aliassen verwijderen</span><span class="sxs-lookup"><span data-stu-id="05b71-200">Delete read-only aliases</span></span>

<span data-ttu-id="05b71-201">Met deze opdracht worden alle aliassen verwijderd uit de huidige sessie, met uitzonde ring van die met de `Constant` eigenschap **Options** van de waarde voor.</span><span class="sxs-lookup"><span data-stu-id="05b71-201">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="05b71-202">`-Force`Met de para meter kan de opdracht aliassen verwijderen waarvan de eigenschap **Options** de waarde `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="05b71-202">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="05b71-203">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="05b71-203">Dynamic parameters</span></span>

<span data-ttu-id="05b71-204">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="05b71-204">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="05b71-205">Opties [System. Management. Automation. ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="05b71-205">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="05b71-206">Bepaalt de waarde van de eigenschap **Options** van een alias.</span><span class="sxs-lookup"><span data-stu-id="05b71-206">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="05b71-207">**Geen** : geen opties.</span><span class="sxs-lookup"><span data-stu-id="05b71-207">**None** : No options.</span></span> <span data-ttu-id="05b71-208">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="05b71-208">This value is the default.</span></span>
- <span data-ttu-id="05b71-209">**Constante** : de alias kan niet worden verwijderd en de eigenschappen kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="05b71-209">**Constant** :The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="05b71-210">**Constante** is alleen beschikbaar wanneer u een alias maakt.</span><span class="sxs-lookup"><span data-stu-id="05b71-210">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="05b71-211">U kunt de optie van een bestaande alias niet wijzigen in een **constante**.</span><span class="sxs-lookup"><span data-stu-id="05b71-211">You cannot change the option of an existing alias to **Constant**.</span></span>
- <span data-ttu-id="05b71-212">**Privé** : de alias is alleen zichtbaar in het huidige bereik, niet in de onderliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="05b71-212">**Private** :The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="05b71-213">**ReadOnly** : de eigenschappen van de alias kunnen niet worden gewijzigd, behalve door gebruik te maken van de `-Force` para meter.</span><span class="sxs-lookup"><span data-stu-id="05b71-213">**ReadOnly** :The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="05b71-214">U kunt gebruiken `Remove-Item` om de alias te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="05b71-214">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="05b71-215">**AllScope** : de alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05b71-215">**AllScope** :The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="05b71-216">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="05b71-216">Cmdlets supported</span></span>

- [<span data-ttu-id="05b71-217">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="05b71-217">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="05b71-218">Set-item</span><span class="sxs-lookup"><span data-stu-id="05b71-218">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="05b71-219">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="05b71-219">Using the pipeline</span></span>

<span data-ttu-id="05b71-220">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="05b71-220">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="05b71-221">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="05b71-221">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="05b71-222">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="05b71-222">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="05b71-223">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="05b71-223">Getting help</span></span>

<span data-ttu-id="05b71-224">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="05b71-224">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="05b71-225">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="05b71-225">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="05b71-226">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05b71-226">See also</span></span>

[<span data-ttu-id="05b71-227">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="05b71-227">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="05b71-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="05b71-228">about_Providers</span></span>](../About/about_Providers.md)
