---
description: Configuratie bestanden voor Power shell core, waarbij de Register configuratie wordt vervangen.
keywords: powershell
Locale: en-US
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: fd4467845cf2b895401a55cbb7abd88b7b72af76
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252433"
---
# <a name="about-powershell-config"></a><span data-ttu-id="3a5d9-104">Over Power shell-configuratie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-104">About PowerShell Config</span></span>

## <a name="short-description"></a><span data-ttu-id="3a5d9-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3a5d9-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="3a5d9-106">Configuratie bestanden voor Power shell core, waarbij de Register configuratie wordt vervangen.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-106">Configuration files for PowerShell Core, replacing Registry configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="3a5d9-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3a5d9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="3a5d9-108">Het `powershell.config.json` bestand bevat configuratie-instellingen voor Power shell core.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-108">The `powershell.config.json` file contains configuration settings for PowerShell Core.</span></span> <span data-ttu-id="3a5d9-109">Power shell laadt deze configuratie bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-109">PowerShell loads this configuration at startup.</span></span> <span data-ttu-id="3a5d9-110">De instellingen kunnen tijdens runtime ook worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-110">The settings can also be modified at runtime.</span></span> <span data-ttu-id="3a5d9-111">Voorheen werden deze instellingen opgeslagen in het Windows-REGI ster voor Power shell, maar zijn ze nu opgenomen in een bestand om de configuratie in macOS en Linux in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-111">Previously, these settings were stored in the Windows Registry for PowerShell, but are now contained in a file to enable configuration on macOS and Linux.</span></span>

> [!WARNING]
> <span data-ttu-id="3a5d9-112">Als het `powershell.config.json` bestand een ongeldige JSON Power shell bevat, kan een interactieve sessie niet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-112">If the `powershell.config.json` file contains invalid JSON PowerShell cannot start an interactive session.</span></span>
> <span data-ttu-id="3a5d9-113">Als dit het geval is, moet u het configuratie bestand herstellen.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-113">If this occurs, you must fix the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-114">Niet-herkende sleutels of ongeldige waarden in het configuratie bestand worden op de achtergrond genegeerd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-114">Unrecognized keys or invalid values in the configuration file will be silently ignored.</span></span>

### <a name="allusers-shared-configuration"></a><span data-ttu-id="3a5d9-115">AllUsers (gedeelde) configuratie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-115">AllUsers (shared) configuration</span></span>

<span data-ttu-id="3a5d9-116">Een `powershell.config.json` bestand in de `$PSHOME` map definieert de configuratie voor alle Power shell-kern sessies die worden uitgevoerd vanaf die Power shell Core-installatie.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-116">A `powershell.config.json` file in the `$PSHOME` directory defines the configuration for all PowerShell Core sessions running from that PowerShell Core installation.</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-117">De `$PSHOME` locatie wordt gedefinieerd als dezelfde map als de uitvoerende System.Management.Automation.dll-assembly.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-117">The `$PSHOME` location is defined as the same directory as the executing System.Management.Automation.dll assembly.</span></span> <span data-ttu-id="3a5d9-118">Dit geldt ook voor gehoste Power shell SDK-exemplaren.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-118">This applies to hosted PowerShell SDK instances as well.</span></span>

### <a name="currentuser-per-user-configurations"></a><span data-ttu-id="3a5d9-119">Instellingen voor het CurrentUser-configuratie (per gebruiker)</span><span class="sxs-lookup"><span data-stu-id="3a5d9-119">CurrentUser (per-user) configurations</span></span>

<span data-ttu-id="3a5d9-120">U kunt Power shell ook configureren op basis van per gebruiker door het bestand in de map voor het configureren van de gebruikers scope te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-120">You can also configure PowerShell on a per-user basis by placing the file in the user-scope configuration directory.</span></span> <span data-ttu-id="3a5d9-121">De map gebruikers configuratie kan worden gevonden op verschillende platformen met de opdracht `Split-Path $PROFILE.CurrentUserCurrentHost` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-121">The user configuration directory can be found across platforms with the command `Split-Path $PROFILE.CurrentUserCurrentHost`.</span></span>

## <a name="general-configuration-settings"></a><span data-ttu-id="3a5d9-122">Algemene configuratie-instellingen</span><span class="sxs-lookup"><span data-stu-id="3a5d9-122">General configuration settings</span></span>

### <a name="executionpolicy"></a><span data-ttu-id="3a5d9-123">ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="3a5d9-123">ExecutionPolicy</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a5d9-124">Deze configuratie is alleen van toepassing op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-124">This configuration only applies on Windows platforms.</span></span>

<span data-ttu-id="3a5d9-125">Hiermee configureert u het uitvoerings beleid voor Power shell-sessies, waarbij u bepaalt welke scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-125">Configures the execution policy for PowerShell sessions, determining what scripts can be run.</span></span> <span data-ttu-id="3a5d9-126">Power Shell maakt standaard gebruik van het bestaande uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-126">By default, PowerShell uses the existing execution policy.</span></span>

<span data-ttu-id="3a5d9-127">Voor AllUsers-configuraties wordt hiermee het beleid voor het uitvoeren van **LocalMachine** ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-127">For AllUsers configurations, this sets the **LocalMachine** execution policy.</span></span>
<span data-ttu-id="3a5d9-128">Hiermee wordt het beleid voor het uitvoeren **van CurrentUser ingesteld** .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-128">For CurrentUser configurations, this sets the **CurrentUser** execution policy.</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-129">De [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet wijzigt deze instelling in het configuratie bestand ALLUSERS wanneer deze wordt aangeroepen met `-Scope LocalMachine` en wijzigt deze instelling in het bestand van het bestand CurrentUser wanneer aangeroepen met `-Scope CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-129">The [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet modifies this setting in the AllUsers configuration file when invoked with `-Scope LocalMachine`, and modifies this setting in the CurrentUser configuration file when invoked with `-Scope CurrentUser`.</span></span>

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

<span data-ttu-id="3a5d9-130">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-130">Where:</span></span>

- <span data-ttu-id="3a5d9-131">`<shell-id>` verwijst naar de ID van de huidige Power shell-host.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-131">`<shell-id>` refers to the ID of the current PowerShell host.</span></span>
  <span data-ttu-id="3a5d9-132">Voor de normale Power shell Core is dit `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-132">For normal PowerShell Core, this is `Microsoft.PowerShell`.</span></span>
  <span data-ttu-id="3a5d9-133">In een Power shell-sessie kunt u deze detecteren met `$ShellId` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-133">In any PowerShell session, you can discover it with `$ShellId`.</span></span>
- <span data-ttu-id="3a5d9-134">`<execution-policy>` verwijst naar een geldige naam voor het uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-134">`<execution-policy>` refers to a valid execution policy name.</span></span>

<span data-ttu-id="3a5d9-135">In het volgende voor beeld wordt het uitvoerings beleid van Power shell ingesteld op `RemoteSigned` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-135">The following example sets the execution policy of PowerShell to `RemoteSigned`.</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

<span data-ttu-id="3a5d9-136">In Windows kunt u de equivalente register sleutels vinden in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` onder `HKEY_LOCAL_MACHINE` en `HKEY_CURRENT_USER` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-136">In Windows, the equivalent registry keys can be found in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`.</span></span>

### <a name="psmodulepath"></a><span data-ttu-id="3a5d9-137">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="3a5d9-137">PSModulePath</span></span>

<span data-ttu-id="3a5d9-138">Hiermee wordt een PSModulePath-onderdeel voor deze Power shell-sessie onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-138">Overrides a PSModulePath component for this PowerShell session.</span></span> <span data-ttu-id="3a5d9-139">Als de configuratie voor de huidige gebruiker is, stelt het pad van de CurrentUser-module in.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-139">If the configuration is for the current user, sets the CurrentUser module path.</span></span> <span data-ttu-id="3a5d9-140">Als de configuratie voor alle gebruikers is ingesteld, stelt het pad naar de AllUser-module in.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-140">If the configuration is for all users, sets the AllUser module path.</span></span>

> [!WARNING]
> <span data-ttu-id="3a5d9-141">Als u een pad naar een AllUsers of een CurrentUser-module configureert, wordt de installatie locatie met het bereik voor PowerShellGet-modules zoals [installatie-module](/powershell/module/powershellget/install-module)niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-141">Configuring an AllUsers or CurrentUser module path here will not change the scoped installation location for PowerShellGet modules like [Install-Module](/powershell/module/powershellget/install-module).</span></span>
> <span data-ttu-id="3a5d9-142">Deze cmdlets gebruiken altijd de *standaard* module paden.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-142">These cmdlets always use the *default* module paths.</span></span>

<span data-ttu-id="3a5d9-143">Als er geen waarde is ingesteld, wordt de standaard waarde voor het desbetreffende padcomponent-onderdeel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-143">If no value is set, the default value for the respective module path component will be used.</span></span> <span data-ttu-id="3a5d9-144">Zie [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) voor meer informatie over deze standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-144">See [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) for more details on these defaults.</span></span>

<span data-ttu-id="3a5d9-145">Met deze instelling kunt u omgevings variabelen gebruiken door ze in te sluiten tussen `%` tekens, zoals `"%HOME%\Documents\PowerShell\Modules"` op dezelfde manier als cmd toestaat.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-145">This setting allows environment variables to be used by embedding them between `%` characters, like `"%HOME%\Documents\PowerShell\Modules"`, in the same way as CMD allows.</span></span> <span data-ttu-id="3a5d9-146">Deze syntaxis is ook van toepassing op Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-146">This syntax also applies on Linux and macOS.</span></span> <span data-ttu-id="3a5d9-147">Hieronder vindt u voor beelden.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-147">See below for examples.</span></span>

```Schema
"PSModulePath": "<ps-module-path>"
```

<span data-ttu-id="3a5d9-148">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-148">Where:</span></span>

- <span data-ttu-id="3a5d9-149">`<ps-module-path>` is het absolute pad naar een module directory.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-149">`<ps-module-path>` is the absolute path to a module directory.</span></span> <span data-ttu-id="3a5d9-150">Voor alle gebruikers configuraties is dit de map AllUsers Shared module.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-150">For all user configurations, this is the AllUsers shared module directory.</span></span> <span data-ttu-id="3a5d9-151">Voor de huidige gebruikers configuraties is dit de map van de CurrentUser-module.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-151">For current user configurations, this is CurrentUser module directory.</span></span>

<span data-ttu-id="3a5d9-152">In dit voor beeld ziet u een PSModulePath-configuratie voor een Windows-omgeving:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-152">This example shows a PSModulePath configuration for a Windows environment:</span></span>

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

<span data-ttu-id="3a5d9-153">In dit voor beeld ziet u een PSModulePath-configuratie voor een macOS-of Linux-omgeving:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-153">This example shows a PSModulePath configuration for a macOS or Linux environment:</span></span>

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

<span data-ttu-id="3a5d9-154">In dit voor beeld ziet u het insluiten van een omgevings variabele in een PSModulePath-configuratie.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-154">This example shows embedding an environment variable in a PSModulePath configuration.</span></span> <span data-ttu-id="3a5d9-155">Houd er rekening mee dat met behulp `HOME` van de omgevings variabele en het `/` mappen scheidings teken dit werkt in Windows, MacOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-155">Note that using the `HOME` environment variable and the `/` directory separator, this will work on Windows, macOS and Linux.</span></span>

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

<span data-ttu-id="3a5d9-156">In dit voor beeld ziet u het insluiten van een omgevings variabele in een PSModulePath-configuratie die alleen wordt gebruikt voor macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-156">This example shows embedding an environment variable in a PSModulePath configuration that will only work on macOS and Linux:</span></span>

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> <span data-ttu-id="3a5d9-157">Power shell-variabelen kunnen niet worden inge sloten in PSModulePath-configuraties.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-157">PowerShell variables cannot be embedded in PSModulePath configurations.</span></span>
> <span data-ttu-id="3a5d9-158">PSModulePath-configuraties voor Linux en macOS zijn hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-158">PSModulePath configurations on Linux and macOS are case-sensitive.</span></span> <span data-ttu-id="3a5d9-159">Een PSModulePath-configuratie moet geldige mappen scheidings tekens voor het platform gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-159">A PSModulePath configuration must use valid directory separators for the platform.</span></span> <span data-ttu-id="3a5d9-160">Op macOS en Linux betekent dit `/` .</span><span class="sxs-lookup"><span data-stu-id="3a5d9-160">On macOS and Linux, this means `/`.</span></span> <span data-ttu-id="3a5d9-161">In Windows zijn beide `/` en `\` werkt.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-161">On Windows, both `/` and `\` will work.</span></span>

### <a name="experimentalfeatures"></a><span data-ttu-id="3a5d9-162">ExperimentalFeatures</span><span class="sxs-lookup"><span data-stu-id="3a5d9-162">ExperimentalFeatures</span></span>

<span data-ttu-id="3a5d9-163">De namen van de experimentele functies die in Power shell moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-163">The names of the experimental features to enable in PowerShell.</span></span>
<span data-ttu-id="3a5d9-164">Standaard zijn er geen experimentele functies ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-164">By default, no experimental features are enabled.</span></span>
<span data-ttu-id="3a5d9-165">De standaard waarde is een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-165">The default value is an empty array.</span></span>

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

<span data-ttu-id="3a5d9-166">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-166">Where:</span></span>

- <span data-ttu-id="3a5d9-167">`<experimental-feature-name>` is de naam van een experimentele functie die moet worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-167">`<experimental-feature-name>` is the name of an experimental feature to enable.</span></span>

<span data-ttu-id="3a5d9-168">In het volgende voor beeld worden de experimentele functies **PSImplicitRemoting** en **PSUseAbbreviationExpansion** ingeschakeld wanneer Power shell wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-168">The following example enables the **PSImplicitRemoting** and **PSUseAbbreviationExpansion** experimental features when PowerShell starts up.</span></span>

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

<span data-ttu-id="3a5d9-169">Zie [Power shell RFC 29][RFC0029]voor meer informatie over experimentele functies.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-169">For more information on experimental features, see [PowerShell RFC 29][RFC0029].</span></span>

## <a name="non-windows-logging-configuration"></a><span data-ttu-id="3a5d9-170">Configuratie van niet-Windows-logboek registratie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-170">Non-Windows logging configuration</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a5d9-171">De configuratie opties in deze sectie zijn alleen van toepassing op macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-171">The configuration options in this section only apply to macOS and Linux.</span></span>
> <span data-ttu-id="3a5d9-172">Logboek registratie voor Windows wordt beheerd door de Windows-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-172">Logging for Windows is managed by the Windows Event Viewer.</span></span>

<span data-ttu-id="3a5d9-173">De logboek registratie van de Power shell in macOS en Linux kan worden geconfigureerd in het Power shell-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-173">PowerShell's logging on macOS and Linux can be configured in the PowerShell configuration file.</span></span> <span data-ttu-id="3a5d9-174">Zie [over logboek registratie](./about_Logging_Non-Windows.md)voor een volledige beschrijving van Power shell-logboek registratie voor niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-174">For a full description of PowerShell logging for non-Windows systems, see [About Logging](./about_Logging_Non-Windows.md).</span></span>

### <a name="logidentity"></a><span data-ttu-id="3a5d9-175">LogIdentity</span><span class="sxs-lookup"><span data-stu-id="3a5d9-175">LogIdentity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a5d9-176">Deze instelling kan alleen worden gebruikt in macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-176">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="3a5d9-177">Hiermee stelt u de identiteits naam in die wordt gebruikt om naar het systeem logboek te schrijven.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-177">Sets the identity name used to write to the system log.</span></span> <span data-ttu-id="3a5d9-178">De standaard waarde is Power shell.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-178">The default value is "powershell".</span></span>

```Schema
"LogIdentity": "<log-identity>"
```

<span data-ttu-id="3a5d9-179">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-179">Where:</span></span>

- <span data-ttu-id="3a5d9-180">`<log-identity>` is de teken reeks-id die Power shell moet gebruiken voor het schrijven naar syslog.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-180">`<log-identity>` is the string identity that PowerShell should use for writing to syslog.</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-181">U wilt mogelijk verschillende **LogIdentity** -waarden hebben voor elk exemplaar van Power shell dat u hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-181">You may want to have different **LogIdentity** values for each different instance of PowerShell you have installed.</span></span>

<span data-ttu-id="3a5d9-182">In dit voor beeld configureren we de **LogIdentity** voor een preview-release van Power shell.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-182">In this example, we are configuring the **LogIdentity** for a preview release of PowerShell.</span></span>

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a><span data-ttu-id="3a5d9-183">Logniveau</span><span class="sxs-lookup"><span data-stu-id="3a5d9-183">LogLevel</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a5d9-184">Deze instelling kan alleen worden gebruikt in macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-184">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="3a5d9-185">Hiermee geeft u het minimale Ernst niveau op waarmee Power shell moet registreren.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-185">Specifies the minimum severity level at which PowerShell should log.</span></span>

```Schema
"LogLevel": "<log-level>|default"
```

<span data-ttu-id="3a5d9-186">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-186">Where:</span></span>

- <span data-ttu-id="3a5d9-187">`<log-level>` is een van:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-187">`<log-level>` is one of:</span></span>
  - <span data-ttu-id="3a5d9-188">Altijd</span><span class="sxs-lookup"><span data-stu-id="3a5d9-188">Always</span></span>
  - <span data-ttu-id="3a5d9-189">Kritiek</span><span class="sxs-lookup"><span data-stu-id="3a5d9-189">Critical</span></span>
  - <span data-ttu-id="3a5d9-190">Fout</span><span class="sxs-lookup"><span data-stu-id="3a5d9-190">Error</span></span>
  - <span data-ttu-id="3a5d9-191">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="3a5d9-191">Warning</span></span>
  - <span data-ttu-id="3a5d9-192">Informatief</span><span class="sxs-lookup"><span data-stu-id="3a5d9-192">Informational</span></span>
  - <span data-ttu-id="3a5d9-193">Uitgebreid</span><span class="sxs-lookup"><span data-stu-id="3a5d9-193">Verbose</span></span>
  - <span data-ttu-id="3a5d9-194">Fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="3a5d9-194">Debug</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-195">Als u een logboek niveau instelt, worden alle bovenstaande logboek niveaus ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-195">Setting a the log level enables all log levels above it.</span></span>

<span data-ttu-id="3a5d9-196">Als u deze instelling instelt op **standaard** , wordt de standaard waarde geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-196">Setting this setting to **default** will be interpreted as the default value.</span></span>
<span data-ttu-id="3a5d9-197">De standaard waarde is **informatief**.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-197">The default value is **Informational**.</span></span>

<span data-ttu-id="3a5d9-198">In het volgende voor beeld wordt de waarde ingesteld op **uitgebreid**.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-198">The following example sets the value to **Verbose**.</span></span>

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a><span data-ttu-id="3a5d9-199">LogChannels</span><span class="sxs-lookup"><span data-stu-id="3a5d9-199">LogChannels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a5d9-200">Deze instelling kan alleen worden gebruikt in macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-200">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="3a5d9-201">Hiermee wordt bepaald welke registratie kanalen worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-201">Determines which logging channels are enabled.</span></span>

```Schema
"LogChannels": "<log-channel>,..."
```

<span data-ttu-id="3a5d9-202">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-202">Where:</span></span>

- <span data-ttu-id="3a5d9-203">`<log-channel>` is een van:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-203">`<log-channel>` is one of:</span></span>
  - <span data-ttu-id="3a5d9-204">Operationeel: registreert basis informatie over Power shell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="3a5d9-204">Operational - logs basic information about PowerShell activities</span></span>
  - <span data-ttu-id="3a5d9-205">Analytische-registreert meer gedetailleerde diagnostische gegevens</span><span class="sxs-lookup"><span data-stu-id="3a5d9-205">Analytic - logs more detailed diagnostic information</span></span>

<span data-ttu-id="3a5d9-206">De standaard waarde is **operationeel**.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-206">The default value is **Operational**.</span></span> <span data-ttu-id="3a5d9-207">Als u beide kanalen wilt inschakelen, neemt u beide waarden op als één door komma's gescheiden teken reeks.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-207">To enable both channels, include both values as a single comma-separated string.</span></span> <span data-ttu-id="3a5d9-208">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-208">For example:</span></span>

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a><span data-ttu-id="3a5d9-209">LogKeywords</span><span class="sxs-lookup"><span data-stu-id="3a5d9-209">LogKeywords</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a5d9-210">Deze instelling kan alleen worden gebruikt in macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-210">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="3a5d9-211">Hiermee wordt bepaald welke delen van Power shell worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-211">Determines which parts of PowerShell are logged.</span></span> <span data-ttu-id="3a5d9-212">Standaard zijn alle logboek trefwoorden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-212">By default, all log keywords are enabled.</span></span> <span data-ttu-id="3a5d9-213">Als u meerdere tref woorden wilt inschakelen, vermeldt u de waarden in één door komma's gescheiden teken reeks.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-213">To enable multiple keywords, list the values in a single comma-separated string.</span></span>

```Schema
"LogKeywords": "<log-keyword>,..."
```

<span data-ttu-id="3a5d9-214">Waar:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-214">Where:</span></span>

- <span data-ttu-id="3a5d9-215">`<log-keyword>` is een van:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-215">`<log-keyword>` is one of:</span></span>
  - <span data-ttu-id="3a5d9-216">Runs Pace-beheer van runs Pace</span><span class="sxs-lookup"><span data-stu-id="3a5d9-216">Runspace - runspace management</span></span>
  - <span data-ttu-id="3a5d9-217">Pijp lijn-pijplijn bewerkingen</span><span class="sxs-lookup"><span data-stu-id="3a5d9-217">Pipeline - pipeline operations</span></span>
  - <span data-ttu-id="3a5d9-218">Protocol-Communication handling, zoals PSRP</span><span class="sxs-lookup"><span data-stu-id="3a5d9-218">Protocol - communication protocol handling, such as PSRP</span></span>
  - <span data-ttu-id="3a5d9-219">Ondersteuning voor transport lagen, zoals SSH</span><span class="sxs-lookup"><span data-stu-id="3a5d9-219">Transport - transport layer support, such as SSH</span></span>
  - <span data-ttu-id="3a5d9-220">Host-Power shell-host-functionaliteit, bijvoorbeeld interactie met de console</span><span class="sxs-lookup"><span data-stu-id="3a5d9-220">Host - PowerShell host functionality, for example console interaction</span></span>
  - <span data-ttu-id="3a5d9-221">Cmdlets-ingebouwde Power shell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="3a5d9-221">Cmdlets -PowerShell builtin cmdlets</span></span>
  - <span data-ttu-id="3a5d9-222">Logica van serializer-serialisatie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-222">Serializer - serialization logic</span></span>
  - <span data-ttu-id="3a5d9-223">Sessie-Power shell-sessie status</span><span class="sxs-lookup"><span data-stu-id="3a5d9-223">Session - PowerShell session state</span></span>
  - <span data-ttu-id="3a5d9-224">ManagedPlugin-WSMan-invoeg toepassing</span><span class="sxs-lookup"><span data-stu-id="3a5d9-224">ManagedPlugin - WSMan plugin</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-225">Het wordt over het algemeen aangeraden deze waarde uit te stellen, tenzij u probeert een bepaald gedrag in een bekend deel van Power shell op te sporen.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-225">It is generally advised to leave this value unset unless you are trying to diagnose a specific behavior in a known part of PowerShell.</span></span>
> <span data-ttu-id="3a5d9-226">Als u deze waarde wijzigt, wordt alleen de hoeveelheid vastgelegde informatie verkleind.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-226">Changing this value only decreases the amount of information logged.</span></span>

<span data-ttu-id="3a5d9-227">In dit voor beeld wordt de logboek registratie beperkt tot runs Pace-bewerkingen, pijplijn logica en cmdlet-gebruik.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-227">This example limits the logging to runspace operations, pipeline logic, and cmdlet use.</span></span> <span data-ttu-id="3a5d9-228">Alle andere logboek registratie wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-228">All other logging will be omitted.</span></span>

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a><span data-ttu-id="3a5d9-229">Meer voorbeeld configuraties</span><span class="sxs-lookup"><span data-stu-id="3a5d9-229">More example configurations</span></span>

### <a name="example-windows-configuration"></a><span data-ttu-id="3a5d9-230">Voor beeld van Windows-configuratie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-230">Example Windows configuration</span></span>

<span data-ttu-id="3a5d9-231">Voor deze configuratie zijn meer instellingen expliciet ingesteld:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-231">This configuration has more settings explicitly set:</span></span>

- <span data-ttu-id="3a5d9-232">Uitvoerings beleid voor deze Power shell-installatie is `AllSigned`</span><span class="sxs-lookup"><span data-stu-id="3a5d9-232">Execution policy for this PowerShell installation is `AllSigned`</span></span>
- <span data-ttu-id="3a5d9-233">Het pad van de CurrentUser-module wordt ingesteld op een module directory op een gedeeld station</span><span class="sxs-lookup"><span data-stu-id="3a5d9-233">The CurrentUser module path is set to a module directory on a shared drive</span></span>
- <span data-ttu-id="3a5d9-234">De `PSImplicitRemotingBatching` experimentele functie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="3a5d9-234">The `PSImplicitRemotingBatching` experimental feature is enabled</span></span>

> [!NOTE]
> <span data-ttu-id="3a5d9-235">De `ExecutionPolicy` instellingen en worden `PSModulePath` hier alleen op een Windows-platform toegepast, omdat het pad naar de module gebruik maakt van `\` `;` scheidings tekens en het uitvoerings beleid niet `Unrestricted` (het enige beleid dat is toegestaan op UNIX-achtige platformen).</span><span class="sxs-lookup"><span data-stu-id="3a5d9-235">The `ExecutionPolicy` and `PSModulePath` settings here would only work on a Windows platform, since the module path uses `\` and `;` separator characters and the execution policy is not `Unrestricted` (the only policy allowed on UNIX-like platforms).</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a><span data-ttu-id="3a5d9-236">Voor beeld van niet-Windows-configuratie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-236">Example non-Windows configuration</span></span>

<span data-ttu-id="3a5d9-237">Met deze configuratie wordt een aantal opties ingesteld die alleen in macOS of Linux werken:</span><span class="sxs-lookup"><span data-stu-id="3a5d9-237">This configuration sets a number of options that only work in macOS or Linux:</span></span>

- <span data-ttu-id="3a5d9-238">Het pad naar de CurrentUser-module is ingesteld op een aangepaste module directory in `$HOME`</span><span class="sxs-lookup"><span data-stu-id="3a5d9-238">The CurrentUser module path is set to a custom module directory in `$HOME`</span></span>
- <span data-ttu-id="3a5d9-239">De functie **PSImplicitRemotingBatching** experimentele is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="3a5d9-239">The **PSImplicitRemotingBatching** experimental feature is enabled</span></span>
- <span data-ttu-id="3a5d9-240">Het Power shell-logboek niveau is ingesteld op **uitgebreid** , voor meer logboek registratie</span><span class="sxs-lookup"><span data-stu-id="3a5d9-240">The PowerShell logging level is set to **Verbose** , for more logging</span></span>
- <span data-ttu-id="3a5d9-241">Met deze Power shell-installatie wordt er naar de logboeken geschreven met de **Home-Power shell-** identiteit.</span><span class="sxs-lookup"><span data-stu-id="3a5d9-241">This PowerShell installation writes to the logs using the **home-powershell** identity.</span></span>

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a><span data-ttu-id="3a5d9-242">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3a5d9-242">See also</span></span>

[<span data-ttu-id="3a5d9-243">Over uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="3a5d9-243">About Execution Policies</span></span>](./about_Execution_Policies.md)

[<span data-ttu-id="3a5d9-244">Over automatische variabelen</span><span class="sxs-lookup"><span data-stu-id="3a5d9-244">About Automatic Variables</span></span>](./about_Automatic_Variables.md)

[RFC0029]: https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md

