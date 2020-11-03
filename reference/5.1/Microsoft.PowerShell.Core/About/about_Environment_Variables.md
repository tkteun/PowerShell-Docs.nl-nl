---
description: Hierin wordt beschreven hoe u toegang krijgt tot Windows-omgevings variabelen in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 3004e01e59d30005ad2fbfa92897f43471a41384
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252808"
---
# <a name="about-environment-variables"></a><span data-ttu-id="2e665-104">Omgevings variabelen</span><span class="sxs-lookup"><span data-stu-id="2e665-104">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="2e665-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2e665-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2e665-106">Hierin wordt beschreven hoe u toegang krijgt tot Windows-omgevings variabelen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e665-106">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2e665-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2e665-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2e665-108">Omgevings variabelen bevatten informatie over de besturingssysteem omgeving.</span><span class="sxs-lookup"><span data-stu-id="2e665-108">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="2e665-109">Deze informatie bevat details zoals het pad van het besturings systeem, het aantal processors dat wordt gebruikt door het besturings systeem en de locatie van tijdelijke mappen.</span><span class="sxs-lookup"><span data-stu-id="2e665-109">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="2e665-110">De omgevings variabelen slaan gegevens op die worden gebruikt door het besturings systeem en andere Program ma's.</span><span class="sxs-lookup"><span data-stu-id="2e665-110">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="2e665-111">De `WINDIR` omgevings variabele bevat bijvoorbeeld de locatie van de installatiemap van Windows.</span><span class="sxs-lookup"><span data-stu-id="2e665-111">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="2e665-112">Program ma's kunnen een query uitvoeren op de waarde van deze variabele om te bepalen waar de bestanden van het Windows-besturings systeem zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="2e665-112">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="2e665-113">Power shell kan omgevings variabelen openen en beheren in elk van de ondersteunde besturingssysteem platforms.</span><span class="sxs-lookup"><span data-stu-id="2e665-113">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="2e665-114">De provider van de Power shell-omgeving vereenvoudigt dit proces door het weer geven en wijzigen van omgevings variabelen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="2e665-114">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="2e665-115">Omgevings variabelen, in tegens telling tot andere typen variabelen in Power shell, worden overgenomen door onderliggende processen, zoals lokale achtergrond taken en de sessies waarin module leden worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2e665-115">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="2e665-116">Dit zorgt ervoor dat omgevings variabelen goed zijn geschikt voor het opslaan van waarden die nodig zijn voor zowel het bovenliggende als het onderliggende proces.</span><span class="sxs-lookup"><span data-stu-id="2e665-116">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="2e665-117">Omgevings variabelen gebruiken en wijzigen</span><span class="sxs-lookup"><span data-stu-id="2e665-117">Using and changing environment variables</span></span>

<span data-ttu-id="2e665-118">In Windows kunnen omgevings variabelen in drie bereiken worden gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="2e665-118">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="2e665-119">Machine-(of systeem) bereik</span><span class="sxs-lookup"><span data-stu-id="2e665-119">Machine (or System) scope</span></span>
- <span data-ttu-id="2e665-120">Gebruikers bereik</span><span class="sxs-lookup"><span data-stu-id="2e665-120">User scope</span></span>
- <span data-ttu-id="2e665-121">Proces bereik</span><span class="sxs-lookup"><span data-stu-id="2e665-121">Process scope</span></span>

<span data-ttu-id="2e665-122">Het _proces_ bereik bevat de omgevings variabelen die beschikbaar zijn in het huidige proces of Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="2e665-122">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="2e665-123">Deze lijst met variabelen wordt overgenomen van het bovenliggende proces en wordt samengesteld op basis van de variabelen in de _computer_ -en _gebruikers_ bereik.</span><span class="sxs-lookup"><span data-stu-id="2e665-123">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span>

<span data-ttu-id="2e665-124">U kunt de waarden van omgevings variabelen weer geven en wijzigen zonder een cmdlet te gebruiken met behulp van een variabele syntaxis met de omgevings provider.</span><span class="sxs-lookup"><span data-stu-id="2e665-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="2e665-125">Als u de waarde van een omgevings variabele wilt weer geven, gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="2e665-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="2e665-126">Als u bijvoorbeeld de waarde van de `WINDIR` omgevings variabele wilt weer geven, typt u de volgende opdracht achter de Power shell-opdracht prompt:</span><span class="sxs-lookup"><span data-stu-id="2e665-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="2e665-127">In deze syntaxis duidt het dollar teken ( `$` ) aan een variabele en geeft de stationsnaam ( `Env:` ) een omgevings variabele aan, gevolgd door de naam van de variabele ( `windir` ).</span><span class="sxs-lookup"><span data-stu-id="2e665-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="2e665-128">Wanneer u omgevings variabelen in Power shell wijzigt, is de wijziging alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2e665-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="2e665-129">Dit gedrag lijkt op het gedrag van de `Set` opdracht in de Windows-opdracht shell en de `Setenv` opdracht in op UNIX gebaseerde omgevingen.</span><span class="sxs-lookup"><span data-stu-id="2e665-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="2e665-130">Als u waarden in het bereik van de computer of de gebruiker wilt wijzigen, moet u de methoden van de klasse **System. Environment** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2e665-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="2e665-131">Als u wijzigingen wilt aanbrengen in de variabelen van de computer bereik, moet ook over machtigingen beschikken.</span><span class="sxs-lookup"><span data-stu-id="2e665-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="2e665-132">Als u probeert een waarde te wijzigen zonder voldoende machtiging, mislukt de opdracht en wordt een fout weer gegeven in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e665-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="2e665-133">U kunt de waarden van variabelen wijzigen zonder gebruik te maken van een cmdlet met de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="2e665-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="2e665-134">Als u bijvoorbeeld wilt toevoegen `;c:\temp` aan de waarde van de `Path` omgevings variabele, gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="2e665-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="2e665-135">U kunt ook de item-cmdlets gebruiken, zoals `Set-Item` , `Remove-Item` , en `Copy-Item` de waarden van omgevings variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="2e665-135">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="2e665-136">Als u bijvoorbeeld de cmdlet wilt gebruiken `Set-Item` om toe `;c:\temp` te voegen aan de waarde van de `Path` omgevings variabele, gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="2e665-136">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="2e665-137">In deze opdracht wordt de waarde tussen haakjes geplaatst, zodat deze wordt geïnterpreteerd als een eenheid.</span><span class="sxs-lookup"><span data-stu-id="2e665-137">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="2e665-138">Omgevings variabelen waarin voor keuren worden opgeslagen</span><span class="sxs-lookup"><span data-stu-id="2e665-138">Environment variables that store preferences</span></span>

<span data-ttu-id="2e665-139">Met de Power shell-functies kunt u omgevings variabelen gebruiken om gebruikers voorkeuren op te slaan.</span><span class="sxs-lookup"><span data-stu-id="2e665-139">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="2e665-140">Deze variabelen werken als voorkeurs variabelen, maar ze worden overgenomen door onderliggende sessies van de sessies waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2e665-140">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="2e665-141">Zie [about_preference_variables](about_Preference_Variables.md)voor meer informatie over voorkeurs variabelen.</span><span class="sxs-lookup"><span data-stu-id="2e665-141">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="2e665-142">De omgevings variabelen waarin de voor keuren zijn opgeslagen, zijn:</span><span class="sxs-lookup"><span data-stu-id="2e665-142">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="2e665-143">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="2e665-143">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="2e665-144">Slaat de uitvoerings beleidset voor de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="2e665-144">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="2e665-145">Deze omgevings variabele bestaat alleen wanneer u een uitvoerings beleid voor één sessie instelt.</span><span class="sxs-lookup"><span data-stu-id="2e665-145">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="2e665-146">U kunt dit op twee verschillende manieren doen.</span><span class="sxs-lookup"><span data-stu-id="2e665-146">You can do this in two different ways.</span></span>

  - <span data-ttu-id="2e665-147">Start een sessie vanaf de opdracht regel met behulp van de para meter **ExecutionPolicy** om het uitvoerings beleid voor de sessie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="2e665-147">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="2e665-148">Gebruik de `Set-ExecutionPolicy` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e665-148">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="2e665-149">Gebruik de bereik parameter met de waarde ' process '.</span><span class="sxs-lookup"><span data-stu-id="2e665-149">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="2e665-150">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e665-150">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="2e665-151">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="2e665-151">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="2e665-152">Power shell biedt controle over het bestand dat wordt gebruikt voor het opslaan van gegevens over modules en de bijbehorende cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2e665-152">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="2e665-153">De cache wordt tijdens het opstarten gelezen tijdens het zoeken naar een opdracht en wordt ergens op een achtergrond thread geschreven nadat een module is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="2e665-153">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="2e665-154">De standaard locatie van de cache is:</span><span class="sxs-lookup"><span data-stu-id="2e665-154">Default location of the cache is:</span></span>

  - `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`

  <span data-ttu-id="2e665-155">De standaard bestandsnaam voor de cache is `ModuleAnalysisCache` .</span><span class="sxs-lookup"><span data-stu-id="2e665-155">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="2e665-156">Als u de standaard locatie van de cache wilt wijzigen, stelt u de omgevings variabele in voordat u Power shell start.</span><span class="sxs-lookup"><span data-stu-id="2e665-156">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="2e665-157">Wijzigingen in deze omgevings variabele zijn alleen van invloed op onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="2e665-157">Changes to this environment variable only affect child processes.</span></span>
  <span data-ttu-id="2e665-158">De waarde moet een volledig pad (inclusief bestands naam) zijn dat Power shell toestemming heeft om bestanden te maken en te schrijven.</span><span class="sxs-lookup"><span data-stu-id="2e665-158">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2e665-159">Als de opdracht detectie niet correct werkt, bijvoorbeeld IntelliSense opdrachten bevat die niet bestaan, kunt u het cache bestand verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2e665-159">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="2e665-160">De cache wordt opnieuw gemaakt wanneer u Power shell de volgende keer start.</span><span class="sxs-lookup"><span data-stu-id="2e665-160">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="2e665-161">Als u de bestands cache wilt uitschakelen, stelt u deze waarde in op een ongeldige locatie, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2e665-161">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="2e665-162">Hiermee stelt u het pad naar het **nul** -apparaat in.</span><span class="sxs-lookup"><span data-stu-id="2e665-162">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="2e665-163">Power shell kan niet naar het pad schrijven, maar er is geen fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2e665-163">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="2e665-164">U kunt de fouten zien die zijn gerapporteerd met behulp van een tracering:</span><span class="sxs-lookup"><span data-stu-id="2e665-164">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="2e665-165">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="2e665-165">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="2e665-166">Wanneer u de module analyse cache afschrijft, controleert Power shell op modules die niet meer bestaan om een onnodig grote cache te voor komen.</span><span class="sxs-lookup"><span data-stu-id="2e665-166">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="2e665-167">Soms zijn deze controles niet gewenst, in welk geval u deze kunt uitschakelen door deze omgevings variabele in te stellen op `1` .</span><span class="sxs-lookup"><span data-stu-id="2e665-167">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="2e665-168">Het instellen van deze omgevings variabele wordt direct van kracht in het huidige proces.</span><span class="sxs-lookup"><span data-stu-id="2e665-168">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="2e665-169">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="2e665-169">PSModulePath</span></span>

  <span data-ttu-id="2e665-170">De `$env:PSModulePath` omgevings variabele bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="2e665-170">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="2e665-171">De doel locaties die worden toegewezen aan, `$env:PSModulePath` zijn standaard:</span><span class="sxs-lookup"><span data-stu-id="2e665-171">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="2e665-172">Locaties voor het hele systeem: deze mappen bevatten modules die worden geleverd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e665-172">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="2e665-173">De modules worden opgeslagen op de `$PSHOME\Modules` locatie.</span><span class="sxs-lookup"><span data-stu-id="2e665-173">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="2e665-174">Dit is ook de locatie waar de Windows-beheer modules worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2e665-174">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="2e665-175">Door de gebruiker geïnstalleerde modules: Dit zijn de modules die door de gebruiker zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2e665-175">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="2e665-176">`Install-Module` heeft een **bereik** parameter waarmee u kunt opgeven of de module is geïnstalleerd voor de huidige gebruiker of voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="2e665-176">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="2e665-177">Zie [install-module](xref:PowerShellGet.Install-Module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e665-177">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="2e665-178">In Windows is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME\Documents\PowerShell\Modules` map.</span><span class="sxs-lookup"><span data-stu-id="2e665-178">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="2e665-179">De locatie van het **ALLUSERS** bereik is `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="2e665-179">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>

  <span data-ttu-id="2e665-180">Daarnaast kunnen installatie Programma's waarmee modules in andere directory's worden geïnstalleerd, zoals de map Program Files, hun locaties toevoegen aan de waarde van `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="2e665-180">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="2e665-181">Zie [about_PSModulePath](about_PSModulePath.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e665-181">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="2e665-182">Omgevings variabelen beheren</span><span class="sxs-lookup"><span data-stu-id="2e665-182">Managing environment variables</span></span>

<span data-ttu-id="2e665-183">Power shell biedt verschillende methoden voor het beheren van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="2e665-183">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="2e665-184">Het omgevings provider station</span><span class="sxs-lookup"><span data-stu-id="2e665-184">The Environment provider drive</span></span>
- <span data-ttu-id="2e665-185">De item-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2e665-185">The Item cmdlets</span></span>
- <span data-ttu-id="2e665-186">De klasse .NET **System. Environment**</span><span class="sxs-lookup"><span data-stu-id="2e665-186">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="2e665-187">In Windows, het configuratie scherm van het systeem</span><span class="sxs-lookup"><span data-stu-id="2e665-187">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="2e665-188">De omgevings provider gebruiken</span><span class="sxs-lookup"><span data-stu-id="2e665-188">Using the Environment provider</span></span>

<span data-ttu-id="2e665-189">Elke omgevings variabele wordt vertegenwoordigd door een instantie van de klasse **System. Collections. Dictionary entry** .</span><span class="sxs-lookup"><span data-stu-id="2e665-189">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="2e665-190">In elk **Dictionary entry** -object is de naam van de omgevings variabele de woorden lijst sleutel.</span><span class="sxs-lookup"><span data-stu-id="2e665-190">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="2e665-191">De waarde van de variabele is de woordenlijst waarde.</span><span class="sxs-lookup"><span data-stu-id="2e665-191">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="2e665-192">Gebruik de cmdlet om de eigenschappen en methoden van het object weer te geven die een omgevings variabele in Power shell vertegenwoordigen `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2e665-192">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="2e665-193">Als u bijvoorbeeld de methoden en eigenschappen van alle objecten in het station wilt weer geven `Env:` , typt u:</span><span class="sxs-lookup"><span data-stu-id="2e665-193">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="2e665-194">De provider van de Power shell-omgeving biedt toegang tot omgevings variabelen in een Power Shell-station (het `Env:` station).</span><span class="sxs-lookup"><span data-stu-id="2e665-194">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="2e665-195">Dit station ziet er ongeveer uit als een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="2e665-195">This drive looks much like a file system drive.</span></span> <span data-ttu-id="2e665-196">Als u naar het `Env:` station wilt gaan, typt u:</span><span class="sxs-lookup"><span data-stu-id="2e665-196">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="2e665-197">Gebruik de cmdlets voor inhoud om de waarden van een omgevings variabele op te halen of in te stellen.</span><span class="sxs-lookup"><span data-stu-id="2e665-197">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="2e665-198">U kunt de omgevings variabelen in het `Env:` station weer geven vanuit elk ander Power Shell-station en u kunt naar het `Env:` station gaan om de omgevings variabelen weer te geven en te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="2e665-198">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="2e665-199">Item-cmdlets gebruiken</span><span class="sxs-lookup"><span data-stu-id="2e665-199">Using Item cmdlets</span></span>

<span data-ttu-id="2e665-200">Wanneer u verwijst naar een omgevings variabele, typt u de `Env:` naam van het station gevolgd door de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="2e665-200">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="2e665-201">Als u bijvoorbeeld de waarde van de `COMPUTERNAME` omgevings variabele wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="2e665-201">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="2e665-202">Als u de waarden van alle omgevings variabelen wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="2e665-202">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="2e665-203">Omdat omgevings variabelen geen onderliggende items hebben, is de uitvoer van `Get-Item` en `Get-ChildItem` is dezelfde.</span><span class="sxs-lookup"><span data-stu-id="2e665-203">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="2e665-204">Standaard worden de omgevings variabelen in Power shell weer gegeven in de volg orde waarin ze worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2e665-204">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="2e665-205">Als u de lijst met omgevings variabelen wilt sorteren op naam van variabele, pipet u de uitvoer van een `Get-ChildItem` opdracht naar de `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e665-205">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2e665-206">Typ bijvoorbeeld van elk Power Shell-station:</span><span class="sxs-lookup"><span data-stu-id="2e665-206">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="2e665-207">U kunt ook naar het `Env:` station gaan met behulp van de `Set-Location` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="2e665-207">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="2e665-208">Wanneer u zich in het station bevindt `Env:` , kunt u de `Env:` naam van het station weglaten uit het pad.</span><span class="sxs-lookup"><span data-stu-id="2e665-208">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="2e665-209">Als u bijvoorbeeld alle omgevings variabelen wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="2e665-209">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="2e665-210">Als u de waarde van de variabele wilt weer geven in `COMPUTERNAME` het `Env:` station, typt u:</span><span class="sxs-lookup"><span data-stu-id="2e665-210">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="2e665-211">Wijzigingen in omgevings variabelen opslaan</span><span class="sxs-lookup"><span data-stu-id="2e665-211">Saving changes to environment variables</span></span>

<span data-ttu-id="2e665-212">Als u een permanente wijziging wilt aanbrengen in een omgevings variabele in Windows, gebruikt u het configuratie scherm van het systeem.</span><span class="sxs-lookup"><span data-stu-id="2e665-212">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="2e665-213">Selecteer **geavanceerde systeem instellingen**.</span><span class="sxs-lookup"><span data-stu-id="2e665-213">Select **Advanced System Settings**.</span></span> <span data-ttu-id="2e665-214">Klik op het tabblad **Geavanceerd** op **omgevings variabele...**. U kunt bestaande omgevings variabelen toevoegen of bewerken in de scopes van de **gebruiker** en het **systeem** (machine).</span><span class="sxs-lookup"><span data-stu-id="2e665-214">On the **Advanced** tab, click **Environment Variable...**. You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="2e665-215">Windows schrijft deze waarden naar het REGI ster, zodat ze behouden blijven in sessies en het opnieuw opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="2e665-215">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="2e665-216">U kunt ook omgevings variabelen toevoegen of wijzigen in uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="2e665-216">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="2e665-217">Deze methode werkt voor elke versie van Power shell op elk ondersteund platform.</span><span class="sxs-lookup"><span data-stu-id="2e665-217">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="2e665-218">Methoden van System. Environment gebruiken</span><span class="sxs-lookup"><span data-stu-id="2e665-218">Using System.Environment methods</span></span>

<span data-ttu-id="2e665-219">De klasse **System. Environment** biedt **GetEnvironmentVariable** -en **SetEnvironmentVariable** -methoden waarmee u het bereik van de variabele kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="2e665-219">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="2e665-220">In het volgende voor beeld wordt de methode **GetEnvironmentVariable** gebruikt om de instelling van de computer `PSModulePath` en de methode **SetEnvironmentVariable** toe te voegen aan de `C:\Program Files\Fabrikam\Modules` waarde.</span><span class="sxs-lookup"><span data-stu-id="2e665-220">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="2e665-221">Zie [omgevings methoden](/dotnet/api/system.environment)voor meer informatie over de methoden van de klasse **System. Environment** .</span><span class="sxs-lookup"><span data-stu-id="2e665-221">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e665-222">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="2e665-222">SEE ALSO</span></span>

- [<span data-ttu-id="2e665-223">Omgeving (provider)</span><span class="sxs-lookup"><span data-stu-id="2e665-223">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="2e665-224">about_Modules</span><span class="sxs-lookup"><span data-stu-id="2e665-224">about_Modules</span></span>](about_Modules.md)
