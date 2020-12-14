---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: 0ec31d32ef73108b53b18b529cc93aa80787fe25
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706050"
---
# <span data-ttu-id="12e95-102">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="12e95-102">Register-PSSessionConfiguration</span></span>

## <span data-ttu-id="12e95-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="12e95-103">SYNOPSIS</span></span>
<span data-ttu-id="12e95-104">Hiermee maakt en registreert u een nieuwe sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-104">Creates and registers a new session configuration.</span></span>

## <span data-ttu-id="12e95-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="12e95-105">SYNTAX</span></span>

### <span data-ttu-id="12e95-106">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="12e95-106">NameParameterSet (Default)</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12e95-107">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="12e95-107">AssemblyNameParameterSet</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12e95-108">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="12e95-108">SessionConfigurationFile</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12e95-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="12e95-109">DESCRIPTION</span></span>

<span data-ttu-id="12e95-110">De `Register-PSSessionConfiguration` cmdlet maakt en registreert een nieuwe sessie configuratie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="12e95-110">The `Register-PSSessionConfiguration` cmdlet creates and registers a new session configuration on the local computer.</span></span> <span data-ttu-id="12e95-111">Dit is een geavanceerde cmdlet die u kunt gebruiken om aangepaste sessies voor externe gebruikers te maken.</span><span class="sxs-lookup"><span data-stu-id="12e95-111">This is an advanced cmdlet that you can use to create custom sessions for remote users.</span></span>

<span data-ttu-id="12e95-112">Elke Power shell-sessie (**PSSession**) maakt gebruik van een sessie configuratie, ook wel bekend als een eind punt.</span><span class="sxs-lookup"><span data-stu-id="12e95-112">Every PowerShell session (**PSSession**) uses a session configuration, also known as an endpoint.</span></span>
<span data-ttu-id="12e95-113">Wanneer gebruikers een sessie maken die verbinding maakt met de computer, kunnen ze een sessie configuratie selecteren of de standaard sessie configuratie gebruiken die wordt geregistreerd wanneer u externe communicatie van Power shell inschakelt.</span><span class="sxs-lookup"><span data-stu-id="12e95-113">When users create a session that connects to the computer, they can select a session configuration or use the default session configuration that is registered when you enable PowerShell remoting.</span></span>
<span data-ttu-id="12e95-114">Gebruikers kunnen ook de $PSSessionConfigurationName voorkeurs variabele instellen, waarmee een standaard configuratie wordt opgegeven voor externe sessies die zijn gemaakt in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-114">Users can also set the $PSSessionConfigurationName preference variable, which specifies a default configuration for remote sessions created in the current session.</span></span>

<span data-ttu-id="12e95-115">De sessie configuratie definieert de omgeving voor de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-115">The session configuration defines the environment for the remote session.</span></span> <span data-ttu-id="12e95-116">De configuratie kan bepalen welke opdrachten en taal elementen beschikbaar zijn in de sessie en kan instellingen bevatten waarmee de computer wordt beveiligd, zoals de onderdelen die de hoeveelheid gegevens beperken die de sessie op afstand kan ontvangen in één object of opdracht.</span><span class="sxs-lookup"><span data-stu-id="12e95-116">The configuration can determine which commands and language elements are available in the session, and it can include settings that protect the computer, such as those that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="12e95-117">De security descriptor van de sessie configuratie bepaalt welke gebruikers gemachtigd zijn om de sessie configuratie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="12e95-117">The security descriptor of the session configuration determines which users have permission to use the session configuration.</span></span>

<span data-ttu-id="12e95-118">U kunt de configuratie-elementen definiëren met behulp van een assembly die een nieuwe configuratie klasse implementeert en met behulp van een script dat in de sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-118">You can define the elements of configuration by using an assembly that implements a new configuration class and by using a script that runs in the session.</span></span> <span data-ttu-id="12e95-119">Vanaf Power Shell 3,0 kunt u ook een sessie configuratie bestand gebruiken om de sessie configuratie te definiëren.</span><span class="sxs-lookup"><span data-stu-id="12e95-119">Beginning in PowerShell 3.0, you can also use a session configuration file to define the session configuration.</span></span>

<span data-ttu-id="12e95-120">Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie over de configuratie van sessies.</span><span class="sxs-lookup"><span data-stu-id="12e95-120">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>
<span data-ttu-id="12e95-121">Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="12e95-121">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

## <span data-ttu-id="12e95-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="12e95-122">EXAMPLES</span></span>

### <span data-ttu-id="12e95-123">Voor beeld 1: een NewShell-sessie configuratie registreren</span><span class="sxs-lookup"><span data-stu-id="12e95-123">Example 1: Register a NewShell session configuration</span></span>

<span data-ttu-id="12e95-124">In dit voor beeld registreren we de **NewShell** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-124">In this example, we register the **NewShell** session configuration.</span></span> <span data-ttu-id="12e95-125">De para meters **assemblyname** en **Application base** geven de locatie van het **MyShell.dll** bestand op, waarmee de cmdlets en providers in de sessie configuratie worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="12e95-125">The **AssemblyName** and **ApplicationBase** parameters specify the location of the **MyShell.dll** file, which specifies the cmdlets and providers in the session configuration.</span></span> <span data-ttu-id="12e95-126">De **ConfigurationTypeName** para meter geeft u de configuratie klasse op die van de assembly moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="12e95-126">The **ConfigurationTypeName** parameter specifies the configuration class to use from the assembly.</span></span>

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

<span data-ttu-id="12e95-127">Als u deze configuratie wilt gebruiken, typt u `New-PSSession -ConfigurationName newshell` .</span><span class="sxs-lookup"><span data-stu-id="12e95-127">To use this configuration, type `New-PSSession -ConfigurationName newshell`.</span></span>

### <span data-ttu-id="12e95-128">Voor beeld 2: een MaintenanceShell-sessie configuratie registreren</span><span class="sxs-lookup"><span data-stu-id="12e95-128">Example 2: Register a MaintenanceShell session configuration</span></span>

<span data-ttu-id="12e95-129">In dit voor beeld wordt de **MaintenanceShell** -sessie configuratie op de lokale computer geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-129">This example registers the **MaintenanceShell** session configuration on the local computer.</span></span> <span data-ttu-id="12e95-130">De **StartupScript** para meter geeft u het `Maintenance.ps1` script op.</span><span class="sxs-lookup"><span data-stu-id="12e95-130">The **StartupScript** parameter specifies the `Maintenance.ps1` script.</span></span>

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

<span data-ttu-id="12e95-131">Wanneer een gebruiker een `New-PSSession` opdracht gebruikt en de **MaintenanceShell** -configuratie selecteert, `Maintenance.ps1` wordt het script in de nieuwe sessie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-131">When a user uses a `New-PSSession` command and selects the **MaintenanceShell** configuration, the `Maintenance.ps1` script runs in the new session.</span></span> <span data-ttu-id="12e95-132">Met het script kan de sessie worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-132">The script can configure the session.</span></span> <span data-ttu-id="12e95-133">Dit omvat het importeren van modules en het instellen van het uitvoerings beleid voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-133">This includes importing modules and setting the execution policy for the session.</span></span> <span data-ttu-id="12e95-134">Als het script fouten genereert, inclusief niet-afsluit fouten, `New-PSSession` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="12e95-134">If the script generates any errors, including non-terminating errors, the `New-PSSession` command fails.</span></span>

### <span data-ttu-id="12e95-135">Voor beeld 3: een sessie configuratie registreren</span><span class="sxs-lookup"><span data-stu-id="12e95-135">Example 3: Register a session configuration</span></span>

<span data-ttu-id="12e95-136">In dit voor beeld wordt de **AdminShell** -sessie configuratie geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-136">This example registers the **AdminShell** session configuration.</span></span>

<span data-ttu-id="12e95-137">De `$sessionParams` variabele is een hashtabel die alle parameter waarden bevat.</span><span class="sxs-lookup"><span data-stu-id="12e95-137">The `$sessionParams` variable is a hashtable containing all the parameter values.</span></span> <span data-ttu-id="12e95-138">Deze hashtabel wordt door gegeven aan de cmdlet met behulp van Power shell splatting.</span><span class="sxs-lookup"><span data-stu-id="12e95-138">This hashtable is passed to the cmdlet using PowerShell splatting.</span></span> <span data-ttu-id="12e95-139">De `Register-PSSessionConfiguration` opdracht gebruikt de para meter **SecurityDescritorSDDL** om de SDDL op te geven in de waarde van de `$sddl` variabele en de para meter **MaximumReceivedObjectSizeMB** om de limiet voor de object grootte te verhogen.</span><span class="sxs-lookup"><span data-stu-id="12e95-139">The `Register-PSSessionConfiguration` command uses the **SecurityDescritorSDDL** parameter to specify the SDDL in the value of the `$sddl` variable and the **MaximumReceivedObjectSizeMB** parameter to increase the object size limit.</span></span> <span data-ttu-id="12e95-140">De para meter **StartupScript** wordt ook gebruikt om een script op te geven waarmee de sessie wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-140">It also uses the **StartupScript** parameter to specify a script that configures the session.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### <span data-ttu-id="12e95-141">Voor beeld 4: een configuratie container element retour neren</span><span class="sxs-lookup"><span data-stu-id="12e95-141">Example 4: Return a configuration container element</span></span>

<span data-ttu-id="12e95-142">In dit voor beeld ziet u hoe u de **MaintenanceShell** -configuratie registreert.</span><span class="sxs-lookup"><span data-stu-id="12e95-142">This example shows how to register the **MaintenanceShell** configuration.</span></span>
<span data-ttu-id="12e95-143">`Register-PSSessionConfiguration` retourneert een **WSManConfigContainerElement** -object dat is opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="12e95-143">`Register-PSSessionConfiguration` returns a **WSManConfigContainerElement** object stored in the `$s` variable.</span></span> <span data-ttu-id="12e95-144">`Format-List` Hiermee worden alle eigenschappen van het geretourneerde object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="12e95-144">`Format-List` displays all the properties of the returned object.</span></span> <span data-ttu-id="12e95-145">De eigenschap **PSPath** geeft aan dat het object is opgeslagen in een map van het WSMan:-station.</span><span class="sxs-lookup"><span data-stu-id="12e95-145">The **PSPath** property shows that the object is stored in a directory of the WSMan: drive.</span></span> <span data-ttu-id="12e95-146">`Get-ChildItem` (alias `dir` ) Hiermee worden de items in het pad weer gegeven `WSMan:\LocalHost\PlugIn` .</span><span class="sxs-lookup"><span data-stu-id="12e95-146">`Get-ChildItem` (alias `dir`) displays the items in the `WSMan:\LocalHost\PlugIn` path.</span></span> <span data-ttu-id="12e95-147">Dit zijn onder andere de nieuwe **MaintenanceShell** -configuratie en de twee standaard configuraties die worden geleverd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="12e95-147">These include the new **MaintenanceShell** configuration and the two default configurations that come with PowerShell.</span></span>

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### <span data-ttu-id="12e95-148">Voor beeld 5: een sessie configuratie registreren met een opstart script</span><span class="sxs-lookup"><span data-stu-id="12e95-148">Example 5: Register a session configuration with a startup script</span></span>

<span data-ttu-id="12e95-149">In dit voor beeld maken en registreren we de **WithProfile** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-149">In this example we create and register the **WithProfile** session configuration.</span></span> <span data-ttu-id="12e95-150">Met de para meter **StartupScript** wordt Power shell omgeleid om het opgegeven script uit te voeren voor elke sessie die gebruikmaakt van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-150">The **StartupScript** parameter directs PowerShell to run the specified script for any session that uses the session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

<span data-ttu-id="12e95-151">Het script bevat één opdracht die gebruikmaakt van punt bronnen om het **CurrentUserAllHosts** -Profiel van de gebruiker uit te voeren in het huidige bereik van de sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-151">The script contains a single command that uses dot sourcing to run the user's **CurrentUserAllHosts** profile in the current scope of the session.</span></span>

<span data-ttu-id="12e95-152">Zie [about_Profiles](./About/about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="12e95-152">For more information about profiles, see [about_Profiles](./About/about_Profiles.md).</span></span> <span data-ttu-id="12e95-153">Zie [about_Scopes](./About/about_Scopes.md)voor meer informatie over punten.</span><span class="sxs-lookup"><span data-stu-id="12e95-153">For more information about dot sourcing, see [about_Scopes](./About/about_Scopes.md).</span></span>

## <span data-ttu-id="12e95-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12e95-154">PARAMETERS</span></span>

### <span data-ttu-id="12e95-155">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="12e95-155">-AccessMode</span></span>

<span data-ttu-id="12e95-156">Hiermee wordt de sessie configuratie in-en uitgeschakeld en wordt bepaald of deze kan worden gebruikt voor externe of lokale sessies op de computer.</span><span class="sxs-lookup"><span data-stu-id="12e95-156">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="12e95-157">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="12e95-157">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12e95-158">Uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="12e95-158">Disabled.</span></span> <span data-ttu-id="12e95-159">Hiermee schakelt u de sessie configuratie uit.</span><span class="sxs-lookup"><span data-stu-id="12e95-159">Disables the session configuration.</span></span> <span data-ttu-id="12e95-160">Het kan niet worden gebruikt voor externe of lokale toegang tot de computer.</span><span class="sxs-lookup"><span data-stu-id="12e95-160">It cannot be used for remote or local access to the computer.</span></span>
- <span data-ttu-id="12e95-161">Lokale.</span><span class="sxs-lookup"><span data-stu-id="12e95-161">Local.</span></span> <span data-ttu-id="12e95-162">Hiermee kunnen gebruikers van de lokale computer de sessie configuratie gebruiken om een lokale loop back-sessie op dezelfde computer te maken, maar wordt de toegang tot externe gebruikers geweigerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-162">Allows users of the local computer to use the session configuration to create a local loopback session on the same computer, but denies access to remote users.</span></span>
- <span data-ttu-id="12e95-163">Beveiligingslek.</span><span class="sxs-lookup"><span data-stu-id="12e95-163">Remote.</span></span> <span data-ttu-id="12e95-164">Hiermee kunnen lokale en externe gebruikers de sessie configuratie gebruiken om sessies te maken en opdrachten uit te voeren op deze computer.</span><span class="sxs-lookup"><span data-stu-id="12e95-164">Allows local and remote users to use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="12e95-165">De standaard waarde is extern.</span><span class="sxs-lookup"><span data-stu-id="12e95-165">The default value is Remote.</span></span>

<span data-ttu-id="12e95-166">Andere cmdlets kunnen de waarde van deze para meter later overschrijven.</span><span class="sxs-lookup"><span data-stu-id="12e95-166">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="12e95-167">`Enable-PSRemoting`Met de cmdlet kunt u bijvoorbeeld externe toegang tot alle sessie configuraties toestaan, de `Enable-PSSessionConfiguration` cmdlet maakt sessie configuraties mogelijk en de `Disable-PSRemoting` cmdlet voor komt externe toegang tot alle sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="12e95-167">For example, the `Enable-PSRemoting` cmdlet allows for remote access to all session configurations, the `Enable-PSSessionConfiguration` cmdlet enables session configurations, and the `Disable-PSRemoting` cmdlet prevents remote access to all session configurations.</span></span>

<span data-ttu-id="12e95-168">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-168">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-169">-Application base</span><span class="sxs-lookup"><span data-stu-id="12e95-169">-ApplicationBase</span></span>

<span data-ttu-id="12e95-170">Hiermee geeft u het pad op van het assembly bestand ( \* . dll) dat is opgegeven in de waarde van de para meter **assemblyname** .</span><span class="sxs-lookup"><span data-stu-id="12e95-170">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span> <span data-ttu-id="12e95-171">Gebruik deze para meter wanneer de waarde van de para meter **assemblyname** geen pad bevat.</span><span class="sxs-lookup"><span data-stu-id="12e95-171">Use this parameter when the value of the **AssemblyName** parameter does not include a path.</span></span> <span data-ttu-id="12e95-172">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="12e95-172">The default is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-173">-Assemblyname</span><span class="sxs-lookup"><span data-stu-id="12e95-173">-AssemblyName</span></span>

<span data-ttu-id="12e95-174">Hiermee geeft u de naam op van een assembly bestand ( \* . dll) waarin het configuratie type is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-174">Specifies the name of an assembly file (\*.dll) in which the configuration type is defined.</span></span> <span data-ttu-id="12e95-175">U kunt het pad van het dll-bestand opgeven in deze para meter of in de waarde van de para meter **Application base** .</span><span class="sxs-lookup"><span data-stu-id="12e95-175">You can specify the path of the .dll in this parameter or in the value of the **ApplicationBase** parameter.</span></span>

<span data-ttu-id="12e95-176">Deze para meter is vereist wanneer u de para meter **ConfigurationTypeName** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="12e95-176">This parameter is required when you specify the **ConfigurationTypeName** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-177">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="12e95-177">-ConfigurationTypeName</span></span>

<span data-ttu-id="12e95-178">Hiermee geeft u de volledig gekwalificeerde naam op van het Microsoft .NET Framework-type dat wordt gebruikt voor deze configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-178">Specifies the fully qualified name of the Microsoft .NET Framework type that is used for this configuration.</span></span> <span data-ttu-id="12e95-179">Voor het type dat u opgeeft, moet de klasse **System. Management. Automation. Remoting. PSSessionConfiguration** worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-179">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="12e95-180">Als u het assembly bestand ( \* . dll) wilt opgeven dat het configuratie type implementeert, geeft u de para meters **Assemblyname** en **Application base** op.</span><span class="sxs-lookup"><span data-stu-id="12e95-180">To specify the assembly file (\*.dll) that implements the configuration type, specify the **AssemblyName** and **ApplicationBase** parameters.</span></span>

<span data-ttu-id="12e95-181">Door een type te maken, kunt u meer aspecten van de sessie configuratie beheren, zoals het weer geven of verbergen van bepaalde para meters van cmdlets of het instellen van de grootte van de gegevens en de object grootte die gebruikers niet kunnen negeren.</span><span class="sxs-lookup"><span data-stu-id="12e95-181">Creating a type lets you control more aspects of the session configuration, such as exposing or hiding certain parameters of cmdlets, or setting data size and object size limits that users cannot override.</span></span>

<span data-ttu-id="12e95-182">Als u deze para meter weglaat, wordt de klasse **DefaultRemotePowerShellConfiguration** gebruikt voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-182">If you omit this parameter, the **DefaultRemotePowerShellConfiguration** class is used for the session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-183">-Force</span><span class="sxs-lookup"><span data-stu-id="12e95-183">-Force</span></span>

<span data-ttu-id="12e95-184">Onderdrukt alle gebruikers vragen en start de **WinRM** -service opnieuw op zonder dat dit wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="12e95-184">Suppresses all user prompts and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="12e95-185">Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.</span><span class="sxs-lookup"><span data-stu-id="12e95-185">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="12e95-186">Geef de para meter **NoServiceRestart** op om het opnieuw opstarten te voor komen en de prompt voor opnieuw opstarten te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="12e95-186">To prevent a restart and suppress the restart prompt, specify the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="12e95-187">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="12e95-187">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="12e95-188">Hiermee geeft u een limiet voor de hoeveelheid gegevens die naar deze computer kan worden verzonden in één externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="12e95-188">Specifies a limit for the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="12e95-189">Voer de gegevens grootte in mega bytes (MB) in.</span><span class="sxs-lookup"><span data-stu-id="12e95-189">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="12e95-190">De standaard waarde is 50 MB.</span><span class="sxs-lookup"><span data-stu-id="12e95-190">The default is 50 MB.</span></span>

<span data-ttu-id="12e95-191">Als een limiet voor gegevens grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt en wordt de waarde van deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-191">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-192">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="12e95-192">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="12e95-193">Hiermee geeft u een limiet voor de hoeveelheid gegevens die in een enkel object naar deze computer kan worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="12e95-193">Specifies a limit for the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="12e95-194">Voer de gegevens grootte in mega bytes in.</span><span class="sxs-lookup"><span data-stu-id="12e95-194">Enter the data size in megabytes.</span></span> <span data-ttu-id="12e95-195">De standaard waarde is 10 MB.</span><span class="sxs-lookup"><span data-stu-id="12e95-195">The default is 10 MB.</span></span>

<span data-ttu-id="12e95-196">Als een limiet voor object grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt en wordt de waarde van deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-196">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-197">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="12e95-197">-ModulesToImport</span></span>

<span data-ttu-id="12e95-198">Hiermee geeft u de modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-198">Specifies the modules that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="12e95-199">Standaard worden alleen **micro soft. Power shell. core** in sessies geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-199">By default, only **Microsoft.PowerShell.Core** is imported into sessions.</span></span> <span data-ttu-id="12e95-200">Tenzij de cmdlets worden uitgesloten, kunt u gebruiken `Import-Module` om modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-200">Unless the cmdlets are excluded, you can use `Import-Module` to add modules to the session.</span></span>

<span data-ttu-id="12e95-201">De modules die zijn opgegeven in deze parameter waarde worden geïmporteerd in toevoegingen aan modules die zijn opgegeven met de para meter **SessionType** en die worden vermeld in de sleutel **ModulesToImport** in het configuratie bestand () van de sessie `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="12e95-201">The modules specified in this parameter value are imported in additions to modules that are specified by the **SessionType** parameter and those listed in the **ModulesToImport** key in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="12e95-202">Instellingen in het bestand met de sessie configuratie kunnen echter de opdrachten die door modules worden geëxporteerd, verbergen of voor komen dat gebruikers ze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="12e95-202">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="12e95-203">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-203">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-204">-Name</span><span class="sxs-lookup"><span data-stu-id="12e95-204">-Name</span></span>

<span data-ttu-id="12e95-205">Hiermee geeft u een naam op voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-205">Specifies a name for the session configuration.</span></span> <span data-ttu-id="12e95-206">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="12e95-206">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-207">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="12e95-207">-NoServiceRestart</span></span>

<span data-ttu-id="12e95-208">De **WinRM** -service wordt niet opnieuw gestart en de prompt voor het opnieuw starten van de service wordt onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="12e95-208">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="12e95-209">Wanneer u een `Register-PSSessionConfiguration` opdracht uitvoert, wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de nieuwe sessie configuratie effectief te maken.</span><span class="sxs-lookup"><span data-stu-id="12e95-209">By default, when you run a `Register-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="12e95-210">Totdat de **WinRM** -service opnieuw is gestart, is de nieuwe sessie configuratie niet effectief.</span><span class="sxs-lookup"><span data-stu-id="12e95-210">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="12e95-211">Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, geeft u de para meter **Force** op.</span><span class="sxs-lookup"><span data-stu-id="12e95-211">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="12e95-212">Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="12e95-212">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="12e95-213">-Path</span><span class="sxs-lookup"><span data-stu-id="12e95-213">-Path</span></span>

<span data-ttu-id="12e95-214">Hiermee geeft u het pad en de bestands naam van een sessie configuratie bestand (. pssc), zoals een gemaakt door `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="12e95-214">Specifies the path and filename of a session configuration file (.pssc), such as one created by `New-PSSessionConfigurationFile`.</span></span> <span data-ttu-id="12e95-215">Als u het pad weglaat, de standaard instelling is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="12e95-215">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="12e95-216">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-216">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-217">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="12e95-217">-ProcessorArchitecture</span></span>

<span data-ttu-id="12e95-218">Hiermee wordt bepaald of een 32-bits of 64-bits versie van het Power Shell-proces wordt gestart in sessies die gebruikmaken van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-218">Determines whether a 32-bit or 64-bit version of the PowerShell process is started in sessions that use this session configuration.</span></span> <span data-ttu-id="12e95-219">De acceptabele waarden voor deze para meter zijn: x86 (32-bits) en AMD64 (64-bits).</span><span class="sxs-lookup"><span data-stu-id="12e95-219">The acceptable values for this parameter are: x86 (32-bit) and AMD64 (64-bit).</span></span> <span data-ttu-id="12e95-220">De standaard waarde is afhankelijk van de processor architectuur van de computer die als host fungeert voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-220">The default value is determined by the processor architecture of the computer that hosts the session configuration.</span></span>

<span data-ttu-id="12e95-221">U kunt deze para meter gebruiken om een 32-bits sessie te maken op een 64-bits computer.</span><span class="sxs-lookup"><span data-stu-id="12e95-221">You can use this parameter to create a 32-bit session on a 64-bit computer.</span></span> <span data-ttu-id="12e95-222">Poging tot het maken van een 64-bits proces op een 32-bits computer mislukt.</span><span class="sxs-lookup"><span data-stu-id="12e95-222">Attempts to create a 64-bit process on a 32-bit computer fail.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-223">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="12e95-223">-PSVersion</span></span>

<span data-ttu-id="12e95-224">Hiermee geeft u de versie van Power shell in sessies die gebruikmaken van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-224">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="12e95-225">De waarde van deze para meter heeft voor rang op de waarde van de sleutel **PowerShellVersion** in het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-225">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="12e95-226">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-226">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-227">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="12e95-227">-RunAsCredential</span></span>

<span data-ttu-id="12e95-228">Hiermee geeft u de referenties op voor opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="12e95-228">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="12e95-229">Standaard worden opdrachten uitgevoerd met de machtigingen van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="12e95-229">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="12e95-230">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-230">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-231">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="12e95-231">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="12e95-232">Hiermee geeft u een SDDL-teken reeks (Security Descriptor Definition Language) op voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-232">Specifies a Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="12e95-233">Deze teken reeks bepaalt de machtigingen die nodig zijn voor het gebruik van de nieuwe sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-233">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="12e95-234">Als u een sessie configuratie wilt gebruiken in een sessie, moeten gebruikers ten minste een machtiging voor uitvoeren (invoke) voor de configuratie hebben.</span><span class="sxs-lookup"><span data-stu-id="12e95-234">To use a session configuration in a session, users must have at least Execute (Invoke) permission for the configuration.</span></span>

<span data-ttu-id="12e95-235">Als de security descriptor complex is, kunt u overwegen de para meter **ShowSecurityDescriptorUI** te gebruiken in plaats van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="12e95-235">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this parameter.</span></span> <span data-ttu-id="12e95-236">U kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="12e95-236">You cannot use both parameters in the same command.</span></span>

<span data-ttu-id="12e95-237">Als u deze para meter weglaat, wordt de hoofd-SDDL voor de **WinRM** -service gebruikt voor deze configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-237">If you omit this parameter, the root SDDL for the **WinRM** service is used for this configuration.</span></span>
<span data-ttu-id="12e95-238">Als u de hoofd-SDDL wilt weer geven of wijzigen, gebruikt u de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="12e95-238">To view or change the root SDDL, use the WSMan provider.</span></span> <span data-ttu-id="12e95-239">Bijvoorbeeld `Get-Item wsman:\localhost\service\rootSDDL`.</span><span class="sxs-lookup"><span data-stu-id="12e95-239">For example `Get-Item wsman:\localhost\service\rootSDDL`.</span></span> <span data-ttu-id="12e95-240">Typ voor meer informatie over de WSMan-provider `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="12e95-240">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-241">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="12e95-241">-SessionTypeOption</span></span>

<span data-ttu-id="12e95-242">Hiermee geeft u typespecifieke opties voor de sessie configuratie op.</span><span class="sxs-lookup"><span data-stu-id="12e95-242">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="12e95-243">Voer een object voor sessie type opties in, zoals het **New psworkflowexecutionoption** -object dat door de `New-PSWorkflowExecutionOption` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-243">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="12e95-244">De opties voor sessies die gebruikmaken van de sessie configuratie, worden bepaald door de waarden van de sessie-opties en de opties voor sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-244">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="12e95-245">Tenzij opgegeven, hebben opties die in de sessie zijn ingesteld, zoals met behulp van de `New-PSSessionOption` cmdlet, voor rang boven de opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-245">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="12e95-246">De waarden van de sessie optie kunnen echter niet groter zijn dan de maximum waarden die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-246">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="12e95-247">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-247">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-248">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="12e95-248">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="12e95-249">Hiermee wordt aangegeven dat met deze cmdlet een eigenschappen venster wordt weer gegeven dat u helpt bij het maken van de SDDL voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-249">Indicates that this cmdlet displays a property sheet that helps you create the SDDL for the session configuration.</span></span> <span data-ttu-id="12e95-250">Het eigenschappen venster wordt weer gegeven nadat u de opdracht hebt ingevoerd `Register-PSSessionConfiguration` en de **WinRM** -service opnieuw hebt gestart.</span><span class="sxs-lookup"><span data-stu-id="12e95-250">The property sheet appears after you enter the `Register-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="12e95-251">Wanneer u de machtigingen voor de configuratie instelt, moet u er rekening mee houden dat gebruikers ten minste de machtiging uitvoeren (invoke) moeten hebben om de sessie configuratie in een sessie te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="12e95-251">When setting the permissions for the configuration, remember that users must have at least Execute (Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="12e95-252">U kunt de para meter **SecurityDescriptorSDDL** en deze para meter niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="12e95-252">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="12e95-253">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="12e95-253">-StartupScript</span></span>

<span data-ttu-id="12e95-254">Hiermee geeft u het volledig gekwalificeerde pad van een Power shell-script op.</span><span class="sxs-lookup"><span data-stu-id="12e95-254">Specifies the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="12e95-255">Het opgegeven script wordt uitgevoerd in de nieuwe sessie die gebruikmaakt van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="12e95-255">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="12e95-256">U kunt het script gebruiken om de sessie verder te configureren.</span><span class="sxs-lookup"><span data-stu-id="12e95-256">You can use the script to additionally configure the session.</span></span> <span data-ttu-id="12e95-257">Als het script een fout genereert, zelfs een niet-afsluit fout, wordt de sessie niet gemaakt en mislukt de `New-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="12e95-257">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-258">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="12e95-258">-ThreadOptions</span></span>

<span data-ttu-id="12e95-259">Hiermee geeft u op hoe threads worden gemaakt en gebruikt wanneer een opdracht in de sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-259">Specifies how threads are created and used when a command runs in the session.</span></span> <span data-ttu-id="12e95-260">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="12e95-260">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12e95-261">Standaard</span><span class="sxs-lookup"><span data-stu-id="12e95-261">Default</span></span>
- <span data-ttu-id="12e95-262">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="12e95-262">ReuseThread</span></span>
- <span data-ttu-id="12e95-263">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="12e95-263">UseCurrentThread</span></span>
- <span data-ttu-id="12e95-264">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="12e95-264">UseNewThread</span></span>

<span data-ttu-id="12e95-265">De standaard waarde is **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="12e95-265">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="12e95-266">Zie [PSThreadOptions Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12e95-266">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-267">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="12e95-267">-TransportOption</span></span>

<span data-ttu-id="12e95-268">Hiermee geeft u de transport optie.</span><span class="sxs-lookup"><span data-stu-id="12e95-268">Specifies the transport option.</span></span>

<span data-ttu-id="12e95-269">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-269">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-270">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="12e95-270">-UseSharedProcess</span></span>

<span data-ttu-id="12e95-271">Gebruik slechts één proces om alle sessies te hosten die door dezelfde gebruiker zijn gestart en dezelfde sessie configuratie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="12e95-271">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="12e95-272">Standaard wordt elke sessie gehost in een eigen proces.</span><span class="sxs-lookup"><span data-stu-id="12e95-272">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="12e95-273">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12e95-273">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="12e95-274">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12e95-274">-Confirm</span></span>

<span data-ttu-id="12e95-275">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="12e95-275">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-276">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12e95-276">-WhatIf</span></span>

<span data-ttu-id="12e95-277">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="12e95-277">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="12e95-278">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-278">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-279">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="12e95-279">-ThreadApartmentState</span></span>

<span data-ttu-id="12e95-280">Hiermee geeft u de Apartment-status van de Threading module moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="12e95-280">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="12e95-281">Acceptabele waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="12e95-281">Acceptable values are:</span></span>

- <span data-ttu-id="12e95-282">Onbekend</span><span class="sxs-lookup"><span data-stu-id="12e95-282">Unknown</span></span>
- <span data-ttu-id="12e95-283">MTA</span><span class="sxs-lookup"><span data-stu-id="12e95-283">MTA</span></span>
- <span data-ttu-id="12e95-284">Wee</span><span class="sxs-lookup"><span data-stu-id="12e95-284">STA</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e95-285">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12e95-285">CommonParameters</span></span>

<span data-ttu-id="12e95-286">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12e95-286">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12e95-287">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12e95-287">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12e95-288">INVOER</span><span class="sxs-lookup"><span data-stu-id="12e95-288">INPUTS</span></span>

### <span data-ttu-id="12e95-289">Geen</span><span class="sxs-lookup"><span data-stu-id="12e95-289">None</span></span>

<span data-ttu-id="12e95-290">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12e95-290">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="12e95-291">UITVOER</span><span class="sxs-lookup"><span data-stu-id="12e95-291">OUTPUTS</span></span>

### <span data-ttu-id="12e95-292">Micro soft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="12e95-292">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>

## <span data-ttu-id="12e95-293">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="12e95-293">NOTES</span></span>

<span data-ttu-id="12e95-294">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="12e95-294">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="12e95-295">Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="12e95-295">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="12e95-296">Met deze cmdlet wordt XML gegenereerd die een invoeg toepassings configuratie voor webservices (WS-Management) vertegenwoordigt en wordt de XML naar WS-Management verzonden, waarmee de invoeg toepassing op de lokale computer ( `New-Item wsman:\localhost\plugin` ) wordt geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="12e95-296">This cmdlet generates XML that represents a Web Services for Management (WS-Management) plug-in configuration and sends the XML to WS-Management, which registers the plug-in on the local computer (`New-Item wsman:\localhost\plugin`).</span></span>

<span data-ttu-id="12e95-297">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="12e95-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="12e95-298">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="12e95-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="12e95-299">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="12e95-299">RELATED LINKS</span></span>

[<span data-ttu-id="12e95-300">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="12e95-300">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="12e95-301">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="12e95-301">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="12e95-302">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="12e95-302">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="12e95-303">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="12e95-303">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="12e95-304">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="12e95-304">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="12e95-305">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="12e95-305">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="12e95-306">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="12e95-306">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="12e95-307">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="12e95-307">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="12e95-308">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="12e95-308">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="12e95-309">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="12e95-309">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
