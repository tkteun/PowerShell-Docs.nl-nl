---
description: Omgeving
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Omgevings provider
ms.openlocfilehash: afa9f17333e09f31b130e24d9ede289f9621faf8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252809"
---
# <a name="environment-provider"></a><span data-ttu-id="b9161-104">Omgevings provider</span><span class="sxs-lookup"><span data-stu-id="b9161-104">Environment provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="b9161-105">Provider naam</span><span class="sxs-lookup"><span data-stu-id="b9161-105">Provider name</span></span>

<span data-ttu-id="b9161-106">Omgeving</span><span class="sxs-lookup"><span data-stu-id="b9161-106">Environment</span></span>

## <a name="drives"></a><span data-ttu-id="b9161-107">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="b9161-107">Drives</span></span>

`Env:`

## <a name="capabilities"></a><span data-ttu-id="b9161-108">Functies</span><span class="sxs-lookup"><span data-stu-id="b9161-108">Capabilities</span></span>

<span data-ttu-id="b9161-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="b9161-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="b9161-110">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="b9161-110">Short description</span></span>

<span data-ttu-id="b9161-111">Biedt toegang tot de Windows-omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="b9161-111">Provides access to the Windows environment variables.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="b9161-112">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="b9161-112">Detailed description</span></span>

<span data-ttu-id="b9161-113">Met de Power shell- **omgevings** provider kunt u omgevings variabelen en-waarden in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b9161-113">The PowerShell **Environment** provider lets you get, add, change, clear, and delete environment variables and values in PowerShell.</span></span>

<span data-ttu-id="b9161-114">**Omgevings** variabelen zijn dynamische variabelen met een naam die de omgeving beschrijven waarin uw Program ma's worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b9161-114">**Environment** variables are dynamically named variables that describe the environment in which your programs run.</span></span> <span data-ttu-id="b9161-115">Windows en Power shell gebruiken omgevings variabelen om permanente gegevens op te slaan die van invloed zijn op de uitvoering van systemen en processen.</span><span class="sxs-lookup"><span data-stu-id="b9161-115">Windows and PowerShell use environment variables to store persistent information that affect system and process execution.</span></span> <span data-ttu-id="b9161-116">In tegens telling tot Power shell-variabelen vallen omgevings variabelen geen bereik beperkingen op.</span><span class="sxs-lookup"><span data-stu-id="b9161-116">Unlike PowerShell variables, environment variables are not subject to scope constraints.</span></span>

<span data-ttu-id="b9161-117">Het **omgevings** station is een platte naam ruimte met de omgevings variabelen die specifiek zijn voor de sessie van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b9161-117">The **Environment** drive is a flat namespace containing the environment variables specific to the current user's session.</span></span> <span data-ttu-id="b9161-118">De omgevings variabelen hebben geen onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="b9161-118">The environment variables have no child items.</span></span>

<span data-ttu-id="b9161-119">De **omgevings** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="b9161-119">The **Environment** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="b9161-120">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="b9161-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="b9161-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="b9161-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="b9161-122">Get-item</span><span class="sxs-lookup"><span data-stu-id="b9161-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="b9161-123">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="b9161-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="b9161-124">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="b9161-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="b9161-125">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="b9161-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="b9161-126">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="b9161-126">Types exposed by this provider</span></span>

<span data-ttu-id="b9161-127">Elke omgevings variabele is een instantie van de klasse [System. Collections. Dictionary entry](/dotnet/api/system.collections.dictionaryentry) .</span><span class="sxs-lookup"><span data-stu-id="b9161-127">Each environment variable is an instance of the [System.Collections.DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) class.</span></span> <span data-ttu-id="b9161-128">De naam van de variabele is de woordenlijst sleutel.</span><span class="sxs-lookup"><span data-stu-id="b9161-128">The name of the variable is the dictionary key.</span></span> <span data-ttu-id="b9161-129">De waarde van de omgevings variabele is de waarde van de woorden lijst.</span><span class="sxs-lookup"><span data-stu-id="b9161-129">The value of the environment variable is the dictionary value.</span></span>

## <a name="navigating-the-environment-drive"></a><span data-ttu-id="b9161-130">Navigeren door het omgevings station</span><span class="sxs-lookup"><span data-stu-id="b9161-130">Navigating the Environment drive</span></span>

<span data-ttu-id="b9161-131">De **omgevings** provider geeft de gegevens opslag in het `Env:` station.</span><span class="sxs-lookup"><span data-stu-id="b9161-131">The **Environment** provider exposes its data store in the `Env:` drive.</span></span> <span data-ttu-id="b9161-132">Als u met omgevings variabelen wilt werken, wijzigt u uw locatie in het `Env:` station ( `Set-Location Env:` ) of werkt u vanaf een ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="b9161-132">To work with environment variables, change your location to the `Env:` drive (`Set-Location Env:`), or work from another PowerShell drive.</span></span> <span data-ttu-id="b9161-133">Als u wilt verwijzen naar een omgevings variabele vanaf een andere locatie, gebruikt u de `Env:` naam van het station in het pad.</span><span class="sxs-lookup"><span data-stu-id="b9161-133">To reference an environment variable from another location, use the `Env:` drive name in the path.</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="b9161-134">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="b9161-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="b9161-135">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b9161-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="b9161-136">U kunt ook met de **omgevings** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="b9161-136">You can also work with the **Environment** provider from any other PowerShell drive.</span></span> <span data-ttu-id="b9161-137">Als u wilt verwijzen naar een omgevings variabele vanaf een andere locatie, gebruikt u de naam van het station `Env:` in het pad.</span><span class="sxs-lookup"><span data-stu-id="b9161-137">To reference an environment variable from another location, use the drive name `Env:` in the path.</span></span>

<span data-ttu-id="b9161-138">De **omgevings** provider stelt ook omgevings variabelen beschikbaar met behulp van een variabele prefix van `$env:` .</span><span class="sxs-lookup"><span data-stu-id="b9161-138">The **Environment** provider also exposes environment variables using a variable prefix of `$env:`.</span></span>  <span data-ttu-id="b9161-139">Met de volgende opdracht wordt de inhoud van de omgevings variabele **Program Files** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9161-139">The following command views the contents of the **ProgramFiles** environment variable.</span></span> <span data-ttu-id="b9161-140">Het `$env:` variabele prefix kan vanuit elk Power Shell-station worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9161-140">The `$env:` variable prefix can be used from any PowerShell drive.</span></span>

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

<span data-ttu-id="b9161-141">U kunt ook de waarde van een omgevings variabele wijzigen met behulp van het `$env:` voor voegsel van de variabele.</span><span class="sxs-lookup"><span data-stu-id="b9161-141">You can also change the value of an environment variable using the `$env:` variable prefix.</span></span>  <span data-ttu-id="b9161-142">Alle wijzigingen die zijn aangebracht, hebben alleen betrekking op de huidige Power shell-sessie zolang deze actief is.</span><span class="sxs-lookup"><span data-stu-id="b9161-142">Any changes made only pertain to the current PowerShell session for as long as it is active.</span></span>

> [!NOTE]
> <span data-ttu-id="b9161-143">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="b9161-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="b9161-144">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="b9161-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="b9161-145">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="b9161-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-environment-variables"></a><span data-ttu-id="b9161-146">Omgevings variabelen ophalen</span><span class="sxs-lookup"><span data-stu-id="b9161-146">Getting environment variables</span></span>

<span data-ttu-id="b9161-147">Met deze opdracht worden alle omgevings variabelen in de huidige sessie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9161-147">This command lists all the environment variables in the current session.</span></span>

```powershell
Get-Item -Path Env:
```

<span data-ttu-id="b9161-148">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b9161-148">You can use this command from any PowerShell drive.</span></span>

<span data-ttu-id="b9161-149">De omgevings provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het gebruikt in combi natie met `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="b9161-149">The Environment provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a><span data-ttu-id="b9161-150">Een geselecteerde omgevings variabele ophalen</span><span class="sxs-lookup"><span data-stu-id="b9161-150">Get a selected environment variable</span></span>

<span data-ttu-id="b9161-151">Met deze opdracht wordt de `WINDIR` omgevings variabele opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9161-151">This command gets the `WINDIR` environment Variable.</span></span>

```powershell
Get-ChildItem -Path Env:windir
```

<span data-ttu-id="b9161-152">U kunt ook de notatie van het variabele voor voegsel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b9161-152">You can also use the variable prefix format as well.</span></span>

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a><span data-ttu-id="b9161-153">Een omgevingsvariabele maken</span><span class="sxs-lookup"><span data-stu-id="b9161-153">Create an environment variable</span></span>

<span data-ttu-id="b9161-154">Met deze opdracht maakt u de `USERMODE` omgevings variabele met de waarde ' niet-beheerder '.</span><span class="sxs-lookup"><span data-stu-id="b9161-154">This command creates the `USERMODE` environment variable with a value of "Non-Admin".</span></span> <span data-ttu-id="b9161-155">De `-Path` parameter waarde maakt het nieuwe item in het `Env:` station.</span><span class="sxs-lookup"><span data-stu-id="b9161-155">The `-Path` parameter value creates the new item in the `Env:` drive.</span></span> <span data-ttu-id="b9161-156">De nieuwe omgevings variabele kan alleen worden gebruikt in de huidige Power shell-sessie zolang deze actief is.</span><span class="sxs-lookup"><span data-stu-id="b9161-156">The new environment variable is only usable in the current PowerShell session for as long as it is active.</span></span>

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a><span data-ttu-id="b9161-157">Een omgevings variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="b9161-157">Changing an environment variable</span></span>

### <a name="rename-an-environment-variable"></a><span data-ttu-id="b9161-158">De naam van een omgevings variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="b9161-158">Rename an environment variable</span></span>

<span data-ttu-id="b9161-159">Met deze opdracht wordt de- `Rename-Item` cmdlet gebruikt om de naam van de `USERMODE` omgevings variabele die u hebt gemaakt, te wijzigen `USERROLE` .</span><span class="sxs-lookup"><span data-stu-id="b9161-159">This command uses the `Rename-Item` cmdlet to change the name of the `USERMODE` environment variable that you created to `USERROLE`.</span></span> <span data-ttu-id="b9161-160">Wijzig niet de naam van een omgevings variabele die door het systeem wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9161-160">Do not change the name of an environment variable that the system uses.</span></span> <span data-ttu-id="b9161-161">Hoewel deze wijzigingen alleen van invloed zijn op de huidige sessie, kunnen ze ervoor zorgen dat het systeem of een programma onjuist werkt.</span><span class="sxs-lookup"><span data-stu-id="b9161-161">Although these changes affect only the current session, they might cause the system or a program to operate incorrectly.</span></span>

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a><span data-ttu-id="b9161-162">Een omgevings variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="b9161-162">Change an environment variable</span></span>

<span data-ttu-id="b9161-163">Met deze opdracht wordt de- `Set-Item` cmdlet gebruikt om de waarde van de `USERROLE` omgevings variabele te wijzigen in ' Administrator '.</span><span class="sxs-lookup"><span data-stu-id="b9161-163">This command uses the `Set-Item` cmdlet to change the value of the `USERROLE` environment variable to "Administrator".</span></span>

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a><span data-ttu-id="b9161-164">Een omgevings variabele kopiëren</span><span class="sxs-lookup"><span data-stu-id="b9161-164">Copy an environment variable</span></span>

<span data-ttu-id="b9161-165">Met deze opdracht wordt de waarde van de `USERROLE` omgevings variabele gekopieerd naar de `USERROLE2` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="b9161-165">This command copies the value of the `USERROLE` environment variable to the `USERROLE2` environment Variable.</span></span>

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a><span data-ttu-id="b9161-166">Een omgevings variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="b9161-166">Remove an environment variable</span></span>

<span data-ttu-id="b9161-167">Met deze opdracht wordt de `USERROLE2` omgevings variabele uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b9161-167">This command deletes the `USERROLE2` environment variable from the current session.</span></span>

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a><span data-ttu-id="b9161-168">Een omgevings variabele met Clear-Item verwijderen</span><span class="sxs-lookup"><span data-stu-id="b9161-168">Remove an environment variable with Clear-Item</span></span>

<span data-ttu-id="b9161-169">Met deze opdracht wordt de `USERROLE` omgevings variabele verwijderd door de waarde ervan te wissen.</span><span class="sxs-lookup"><span data-stu-id="b9161-169">This command deletes the `USERROLE` environment variable by clearing its value.</span></span>

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a><span data-ttu-id="b9161-170">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="b9161-170">Using the pipeline</span></span>

<span data-ttu-id="b9161-171">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b9161-171">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="b9161-172">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="b9161-172">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="b9161-173">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b9161-173">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="b9161-174">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="b9161-174">Getting help</span></span>

<span data-ttu-id="b9161-175">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="b9161-175">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="b9161-176">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="b9161-176">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a><span data-ttu-id="b9161-177">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9161-177">See also</span></span>

[<span data-ttu-id="b9161-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b9161-178">about_Providers</span></span>](../About/about_Providers.md)
