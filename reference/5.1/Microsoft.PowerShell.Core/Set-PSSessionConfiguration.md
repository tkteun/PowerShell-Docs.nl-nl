---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 33773769cd19373764cf4adbe86bb990589948ff
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251477"
---
# <span data-ttu-id="432ce-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="432ce-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="432ce-104">SYNOPSIS</span></span>
<span data-ttu-id="432ce-105">Hiermee wijzigt u de eigenschappen van een geregistreerde sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="432ce-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="432ce-106">SYNTAX</span></span>

### <span data-ttu-id="432ce-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="432ce-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="432ce-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="432ce-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="432ce-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="432ce-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="432ce-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="432ce-110">DESCRIPTION</span></span>

<span data-ttu-id="432ce-111">De `Set-PSSessionConfiguration` cmdlet wijzigt de eigenschappen van de sessie configuraties op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="432ce-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="432ce-112">Gebruik de para meter **name** om de sessie configuratie te identificeren die u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="432ce-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="432ce-113">Gebruik de andere para meters om nieuwe waarden op te geven voor de eigenschappen van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="432ce-114">Als u een eigenschaps waarde uit de configuratie wilt verwijderen en de standaard waarde wilt gebruiken, voert u een lege teken reeks ("") of een waarde van `$Null` voor de bijbehorende para meter in.</span><span class="sxs-lookup"><span data-stu-id="432ce-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="432ce-115">Vanaf Power Shell 3,0 kunt u een configuratie bestand voor de sessie gebruiken om een sessie configuratie te definiëren.</span><span class="sxs-lookup"><span data-stu-id="432ce-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="432ce-116">Deze functie biedt een eenvoudige en Detecteer bare methode voor het instellen en wijzigen van de eigenschappen van sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="432ce-117">Als u een sessie configuratie bestand wilt opgeven, gebruikt u de para meter **Path** van `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="432ce-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="432ce-118">Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="432ce-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="432ce-119">Voor informatie over het maken en wijzigen van een sessie configuratie bestand, raadpleegt u de `New-PSSessionConfigurationFile` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="432ce-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="432ce-120">Met sessie configuraties wordt de omgeving van externe sessies ( **PSSessions** ) gedefinieerd die verbinding maken met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="432ce-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="432ce-121">Elke **PSSession** maakt gebruik van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="432ce-122">De sessie configuratie bepaalt de functies van de **PSSession** , zoals de modules die beschikbaar zijn in de sessie, de cmdlets die mogen worden uitgevoerd, de taal modus, quota en time-outs.</span><span class="sxs-lookup"><span data-stu-id="432ce-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="432ce-123">De security descriptor van de sessie configuratie bepaalt wie de sessie configuratie kan gebruiken om verbinding te maken met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="432ce-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="432ce-124">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="432ce-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="432ce-125">Als u de eigenschappen van een sessie configuratie wilt bekijken, gebruikt u de `Get-PSSessionConfiguration` cmdlet of de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="432ce-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="432ce-126">Typ voor meer informatie over de WSMan-provider `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="432ce-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="432ce-127">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="432ce-127">EXAMPLES</span></span>

### <span data-ttu-id="432ce-128">Voor beeld 1: de thread Apartment-status wijzigen</span><span class="sxs-lookup"><span data-stu-id="432ce-128">Example 1: Change the thread apartment state</span></span>

```
PS C:\> Set-PSSessionConfiguration -Name "MaintenanceShell" -ThreadApartmentState STA
```

<span data-ttu-id="432ce-129">Met deze opdracht wordt de thread Apartment-status in de MaintenanceShell-configuratie gewijzigd in STA.</span><span class="sxs-lookup"><span data-stu-id="432ce-129">This command changes the thread apartment state in the MaintenanceShell configuration to STA.</span></span>
<span data-ttu-id="432ce-130">De wijziging is van kracht wanneer u de **WinRM** -service opnieuw start.</span><span class="sxs-lookup"><span data-stu-id="432ce-130">The change is effective when you restart the **WinRM** service.</span></span>

### <span data-ttu-id="432ce-131">Voor beeld 2: een sessie configuratie maken en wijzigen</span><span class="sxs-lookup"><span data-stu-id="432ce-131">Example 2: Create and change a session configuration</span></span>

<span data-ttu-id="432ce-132">In dit voor beeld ziet u hoe u een opstart script kunt toevoegen aan en verwijderen uit een configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-132">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="432ce-133">Met de eerste opdracht wordt de **AdminShell** -configuratie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="432ce-133">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="432ce-134">Met de tweede opdracht wordt het `AdminConfig.ps1` script aan de configuratie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="432ce-134">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="432ce-135">De wijziging is van kracht wanneer u **WinRM** opnieuw opstart.</span><span class="sxs-lookup"><span data-stu-id="432ce-135">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="432ce-136">Met de derde opdracht wordt het `AdminConfig.ps1` script uit de configuratie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="432ce-136">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="432ce-137">Voor beeld 3: resultaten weer geven</span><span class="sxs-lookup"><span data-stu-id="432ce-137">Example 3: Display results</span></span>

<span data-ttu-id="432ce-138">In dit voor beeld wordt de waarde van de eigenschap **MaximumReceivedObjectSizeMB** verhoogd naar 20.</span><span class="sxs-lookup"><span data-stu-id="432ce-138">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="432ce-139">Met deze opdracht wordt ook gevraagd de **WinRM** -service opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="432ce-139">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="432ce-140">De wijziging is pas van kracht nadat de **WinRM** -service opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="432ce-140">The change is not effective until the **WinRM** service is restarted.</span></span>

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### <span data-ttu-id="432ce-141">Voor beeld 4: resultaten op verschillende manieren weer geven</span><span class="sxs-lookup"><span data-stu-id="432ce-141">Example 4: Display results in different ways</span></span>

<span data-ttu-id="432ce-142">In dit voor beeld wordt `Set-PSSessionConfiguration` het opstart script in de **MaintenanceShell** -sessie configuratie gewijzigd in `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="432ce-142">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="432ce-143">In de uitvoer ziet u de wijziging en wordt u gevraagd de **WinRM** -service opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="432ce-143">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="432ce-144">De reactie is ' y ' (Ja).</span><span class="sxs-lookup"><span data-stu-id="432ce-144">The response is "y" (yes).</span></span>

<span data-ttu-id="432ce-145">`Get-PSSessionConfiguration` Hiermee wordt de **MaintenanceShell** -sessie configuratie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="432ce-145">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="432ce-146">De pijplijn operator (|) verzendt de resultaten van de opdracht naar `Format-List` , waarin alle eigenschappen van het configuratie object in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="432ce-146">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="432ce-147">Vervolgens worden de initialisatie parameters voor de **MaintenanceShell** -configuratie weer gegeven met behulp van de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="432ce-147">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="432ce-148">`Get-ChildItem` (alias `dir` ) Hiermee worden de onderliggende items in het **InitializationParameters** -knoop punt voor de **MaintenanceShell** -invoeg toepassing opgehaald.</span><span class="sxs-lookup"><span data-stu-id="432ce-148">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="432ce-149">Typ voor meer informatie over de WSMan-provider `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="432ce-149">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```
PS> Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

PS> Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *

xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :

PS> dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## <span data-ttu-id="432ce-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="432ce-150">PARAMETERS</span></span>

### <span data-ttu-id="432ce-151">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="432ce-151">-AccessMode</span></span>

<span data-ttu-id="432ce-152">Hiermee wordt de sessie configuratie in-en uitgeschakeld en wordt bepaald of deze kan worden gebruikt voor externe of lokale sessies op de computer.</span><span class="sxs-lookup"><span data-stu-id="432ce-152">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="432ce-153">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="432ce-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="432ce-154">Uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="432ce-154">Disabled.</span></span> <span data-ttu-id="432ce-155">Hiermee schakelt u de sessie configuratie uit.</span><span class="sxs-lookup"><span data-stu-id="432ce-155">Disables the session configuration.</span></span> <span data-ttu-id="432ce-156">Het kan niet worden gebruikt voor externe of lokale toegang tot de computer.</span><span class="sxs-lookup"><span data-stu-id="432ce-156">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="432ce-157">Met deze waarde wordt de eigenschap **enabled** van de sessie configuratie ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` ) ingesteld op **False**.</span><span class="sxs-lookup"><span data-stu-id="432ce-157">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="432ce-158">Lokale.</span><span class="sxs-lookup"><span data-stu-id="432ce-158">Local.</span></span> <span data-ttu-id="432ce-159">Hiermee voegt u een **Network_Deny_All** vermelding toe aan security descriptor van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-159">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="432ce-160">Gebruikers van de lokale computer kunnen de sessie configuratie gebruiken om een lokale loop back-sessie op dezelfde computer te maken, maar externe gebruikers krijgen geen toegang.</span><span class="sxs-lookup"><span data-stu-id="432ce-160">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="432ce-161">Beveiligingslek.</span><span class="sxs-lookup"><span data-stu-id="432ce-161">Remote.</span></span> <span data-ttu-id="432ce-162">Hiermee verwijdert u **Deny_All** en **Network_Deny_All** vermeldingen uit de security descriptors van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-162">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="432ce-163">Gebruikers van lokale en externe computers kunnen de sessie configuratie gebruiken om sessies te maken en opdrachten uit te voeren op deze computer.</span><span class="sxs-lookup"><span data-stu-id="432ce-163">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="432ce-164">De standaard waarde is **extern**.</span><span class="sxs-lookup"><span data-stu-id="432ce-164">The default value is **Remote**.</span></span>

<span data-ttu-id="432ce-165">Andere cmdlets kunnen de waarde van deze para meter later overschrijven.</span><span class="sxs-lookup"><span data-stu-id="432ce-165">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="432ce-166">Met de cmdlet worden bijvoorbeeld `Enable-PSRemoting` alle sessie configuraties op de computer ingeschakeld en externe toegang tot deze computers toegestaan. met de `Disable-PSRemoting` cmdlet wordt alleen lokale toegang tot alle sessie configuraties op de computer toegestaan.</span><span class="sxs-lookup"><span data-stu-id="432ce-166">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="432ce-167">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-167">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-168">-Application base</span><span class="sxs-lookup"><span data-stu-id="432ce-168">-ApplicationBase</span></span>

<span data-ttu-id="432ce-169">Hiermee geeft u het pad op van het assembly bestand ( \* . dll) dat is opgegeven in de waarde van de para meter **assemblyname** .</span><span class="sxs-lookup"><span data-stu-id="432ce-169">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="432ce-170">-Assemblyname</span><span class="sxs-lookup"><span data-stu-id="432ce-170">-AssemblyName</span></span>

<span data-ttu-id="432ce-171">Hiermee geeft u de naam van de assembly.</span><span class="sxs-lookup"><span data-stu-id="432ce-171">Specifies the assembly name.</span></span> <span data-ttu-id="432ce-172">Met deze cmdlet maakt u een sessie configuratie op basis van een klasse die is gedefinieerd in een assembly.</span><span class="sxs-lookup"><span data-stu-id="432ce-172">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="432ce-173">Voer de bestands naam of het volledige pad van een assembly. dll-bestand in dat een sessie configuratie definieert.</span><span class="sxs-lookup"><span data-stu-id="432ce-173">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="432ce-174">Als u alleen de bestands naam opgeeft, kunt u het pad opgeven in de waarde van de para meter **Application base** .</span><span class="sxs-lookup"><span data-stu-id="432ce-174">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

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

### <span data-ttu-id="432ce-175">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="432ce-175">-ConfigurationTypeName</span></span>

<span data-ttu-id="432ce-176">Hiermee geeft u het type sessie configuratie op dat in de assembly in de para meter **assemblyname** is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-176">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="432ce-177">Voor het type dat u opgeeft, moet de klasse **System. Management. Automation. Remoting. PSSessionConfiguration** worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-177">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="432ce-178">Deze para meter is vereist wanneer u de naam van een assembly opgeeft.</span><span class="sxs-lookup"><span data-stu-id="432ce-178">This parameter is required when you specify an assembly name.</span></span>

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

### <span data-ttu-id="432ce-179">-Force</span><span class="sxs-lookup"><span data-stu-id="432ce-179">-Force</span></span>

<span data-ttu-id="432ce-180">Onderdrukt alle gebruikers prompts en start de **WinRM** -service opnieuw op zonder toestemming te vragen.</span><span class="sxs-lookup"><span data-stu-id="432ce-180">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="432ce-181">Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.</span><span class="sxs-lookup"><span data-stu-id="432ce-181">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="432ce-182">Als u het opnieuw opstarten wilt voor komen en de prompt voor opnieuw opstarten wilt onderdrukken, gebruikt u de para meter **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="432ce-182">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="432ce-183">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="432ce-183">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="432ce-184">Hiermee geeft u de limiet op voor de hoeveelheid gegevens die naar deze computer kan worden verzonden in één externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="432ce-184">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="432ce-185">Voer de gegevens grootte in mega bytes (MB) in.</span><span class="sxs-lookup"><span data-stu-id="432ce-185">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="432ce-186">De standaard waarde is 50 MB.</span><span class="sxs-lookup"><span data-stu-id="432ce-186">The default is 50 MB.</span></span>

<span data-ttu-id="432ce-187">Als er een limiet voor gegevens grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt.</span><span class="sxs-lookup"><span data-stu-id="432ce-187">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="432ce-188">De waarde van deze para meter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-188">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="432ce-189">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="432ce-189">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="432ce-190">Hiermee geeft u de limieten op voor de hoeveelheid gegevens die in een enkel object naar deze computer kan worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="432ce-190">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="432ce-191">Voer de gegevens grootte in mega bytes in.</span><span class="sxs-lookup"><span data-stu-id="432ce-191">Enter the data size in megabytes.</span></span> <span data-ttu-id="432ce-192">De standaard waarde is 10 MB.</span><span class="sxs-lookup"><span data-stu-id="432ce-192">The default is 10 MB.</span></span>

<span data-ttu-id="432ce-193">Als een limiet voor object grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt.</span><span class="sxs-lookup"><span data-stu-id="432ce-193">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="432ce-194">De waarde van deze para meter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-194">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="432ce-195">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="432ce-195">-ModulesToImport</span></span>

<span data-ttu-id="432ce-196">Hiermee geeft u de modules en modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-196">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="432ce-197">Voer de naam van de module en module in.</span><span class="sxs-lookup"><span data-stu-id="432ce-197">Enter the module and snap-in names.</span></span>

<span data-ttu-id="432ce-198">Standaard wordt alleen de module **micro soft. Power shell. core** geïmporteerd in sessies, maar tenzij de cmdlets worden uitgesloten, kunt u de `Import-Module` cmdlets en Add-PSSnapin gebruiken om modules en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="432ce-198">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="432ce-199">De modules die zijn opgegeven in deze parameter waarde worden geïmporteerd in toevoegingen aan modules die zijn opgegeven in het sessie configuratie bestand ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="432ce-199">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="432ce-200">Instellingen in het bestand met de sessie configuratie kunnen echter de opdrachten die door modules worden geëxporteerd, verbergen of voor komen dat gebruikers ze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="432ce-200">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="432ce-201">De modules die zijn opgegeven in deze parameter waarde, vervangen de lijst met modules die zijn opgegeven met behulp van de para meter **ModulesToImport** van de `Register-PSSessionConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="432ce-201">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="432ce-202">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-202">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-203">-Name</span><span class="sxs-lookup"><span data-stu-id="432ce-203">-Name</span></span>

<span data-ttu-id="432ce-204">Hiermee geeft u de naam van de sessie configuratie op die u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="432ce-204">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="432ce-205">U kunt deze para meter niet gebruiken om de naam van de sessie configuratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="432ce-205">You cannot use this parameter to change the name of the session configuration.</span></span>

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

### <span data-ttu-id="432ce-206">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="432ce-206">-NoServiceRestart</span></span>

<span data-ttu-id="432ce-207">De **WinRM** -service wordt niet opnieuw gestart en de prompt voor het opnieuw starten van de service wordt onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="432ce-207">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="432ce-208">Wanneer u uitvoert `Set-PSSessionConfiguration` , wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de nieuwe sessie configuratie effectief te maken.</span><span class="sxs-lookup"><span data-stu-id="432ce-208">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="432ce-209">Totdat de **WinRM** -service opnieuw is gestart, is de nieuwe sessie configuratie niet effectief.</span><span class="sxs-lookup"><span data-stu-id="432ce-209">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="432ce-210">Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="432ce-210">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="432ce-211">Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="432ce-211">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="432ce-212">-Path</span><span class="sxs-lookup"><span data-stu-id="432ce-212">-Path</span></span>

<span data-ttu-id="432ce-213">Hiermee geeft u het pad van een sessie configuratie bestand (. pssc), zoals een door de `New-PSSessionConfigurationFile` cmdlet gemaakt.</span><span class="sxs-lookup"><span data-stu-id="432ce-213">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="432ce-214">Als u het pad weglaat, de standaard instelling is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="432ce-214">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="432ce-215">Zie het Help-onderwerp voor de cmdlet voor meer informatie over het wijzigen van een configuratie bestand voor een sessie `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="432ce-215">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="432ce-216">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-217">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="432ce-217">-PSVersion</span></span>

<span data-ttu-id="432ce-218">Hiermee geeft u de versie van Power shell in sessies die gebruikmaken van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-218">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="432ce-219">De waarde van deze para meter heeft voor rang op de waarde van de sleutel **PowerShellVersion** in het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="432ce-219">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="432ce-220">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-220">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-221">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="432ce-221">-RunAsCredential</span></span>

<span data-ttu-id="432ce-222">Hiermee geeft u de referenties op voor opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="432ce-222">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="432ce-223">Standaard worden opdrachten uitgevoerd met de machtigingen van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="432ce-223">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="432ce-224">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-224">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-225">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="432ce-225">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="432ce-226">Hiermee geeft u een andere SDDL-teken reeks (Security Descriptor Definition Language) op voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-226">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="432ce-227">Deze teken reeks bepaalt de machtigingen die nodig zijn voor het gebruik van de nieuwe sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-227">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="432ce-228">Als u een sessie configuratie wilt gebruiken in een sessie, moeten gebruikers ten minste een machtiging voor uitvoeren (invoke) voor de configuratie hebben.</span><span class="sxs-lookup"><span data-stu-id="432ce-228">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="432ce-229">Als u de standaard security descriptor voor de configuratie wilt gebruiken, voert u een lege teken reeks ("") of een waarde van in `$Null` .</span><span class="sxs-lookup"><span data-stu-id="432ce-229">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="432ce-230">De standaard waarde is de hoofd-SDDL in het WSMan:-station.</span><span class="sxs-lookup"><span data-stu-id="432ce-230">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="432ce-231">Als de security descriptor complex is, kunt u overwegen de para meter **ShowSecurityDescriptorUI** te gebruiken in plaats van deze.</span><span class="sxs-lookup"><span data-stu-id="432ce-231">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="432ce-232">U kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="432ce-232">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="432ce-233">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="432ce-233">-SessionTypeOption</span></span>

<span data-ttu-id="432ce-234">Hiermee geeft u typespecifieke opties voor de sessie configuratie op.</span><span class="sxs-lookup"><span data-stu-id="432ce-234">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="432ce-235">Voer een object voor sessie type opties in, zoals het **New psworkflowexecutionoption** -object dat door de `New-PSWorkflowExecutionOption` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-235">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="432ce-236">De opties voor sessies die gebruikmaken van de sessie configuratie, worden bepaald door de waarden van de sessie-opties en de opties voor sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-236">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="432ce-237">Tenzij opgegeven, hebben opties die in de sessie zijn ingesteld, zoals met behulp van de `New-PSSessionOption` cmdlet, voor rang boven de opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-237">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="432ce-238">De waarden van de sessie optie kunnen echter niet groter zijn dan de maximum waarden die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-238">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="432ce-239">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-239">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-240">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="432ce-240">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="432ce-241">Hiermee wordt aangegeven dat deze cmdlet een eigenschappen venster is waarmee u een nieuwe SDDL voor de sessie configuratie kunt maken.</span><span class="sxs-lookup"><span data-stu-id="432ce-241">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="432ce-242">Het eigenschappen venster wordt weer gegeven nadat u de opdracht hebt uitgevoerd `Set-PSSessionConfiguration` en de **WinRM** -service opnieuw hebt gestart.</span><span class="sxs-lookup"><span data-stu-id="432ce-242">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="432ce-243">Wanneer u machtigingen instelt voor de configuratie, moet u er rekening mee houden dat gebruikers ten minste de machtiging voor uitvoeren (invoke) moeten hebben om de sessie configuratie in een sessie te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="432ce-243">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="432ce-244">U kunt de para meter **SecurityDescriptorSDDL** en deze para meter niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="432ce-244">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="432ce-245">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="432ce-245">-StartupScript</span></span>

<span data-ttu-id="432ce-246">Hiermee geeft u het opstart script voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-246">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="432ce-247">Geef het volledig gekwalificeerde pad van een Power shell-script op.</span><span class="sxs-lookup"><span data-stu-id="432ce-247">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="432ce-248">Het opgegeven script wordt uitgevoerd in de nieuwe sessie die gebruikmaakt van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-248">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="432ce-249">Als u een opstart script uit een sessie configuratie wilt verwijderen, voert u een lege teken reeks ("") of een waarde van in `$Null` .</span><span class="sxs-lookup"><span data-stu-id="432ce-249">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="432ce-250">U kunt een opstart script gebruiken om de gebruikers sessie verder te configureren.</span><span class="sxs-lookup"><span data-stu-id="432ce-250">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="432ce-251">Als het script een fout genereert, zelfs een niet-afsluit fout, wordt de sessie niet gemaakt en mislukt de `New-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="432ce-251">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="432ce-252">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="432ce-252">-ThreadApartmentState</span></span>

<span data-ttu-id="432ce-253">Hiermee geeft u de instelling voor de status van de Apartment voor de threads in de sessie.</span><span class="sxs-lookup"><span data-stu-id="432ce-253">Specifies the apartment state setting for the threads in the session.</span></span>
<span data-ttu-id="432ce-254">De acceptabele waarden voor deze para meter zijn: STA, MTA en onbekend.</span><span class="sxs-lookup"><span data-stu-id="432ce-254">The acceptable values for this parameter are: STA, MTA, and Unknown.</span></span>
<span data-ttu-id="432ce-255">De standaard waarde is onbekend.</span><span class="sxs-lookup"><span data-stu-id="432ce-255">The default value is Unknown.</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:
Accepted values: STA, MTA, Unknown

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="432ce-256">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="432ce-256">-ThreadOptions</span></span>

<span data-ttu-id="432ce-257">Hiermee geeft u de instelling thread opties in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-257">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="432ce-258">Deze instelling bepaalt hoe threads worden gemaakt en gebruikt wanneer een opdracht in de sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-258">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="432ce-259">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="432ce-259">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="432ce-260">Standaard</span><span class="sxs-lookup"><span data-stu-id="432ce-260">Default</span></span>
- <span data-ttu-id="432ce-261">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="432ce-261">ReuseThread</span></span>
- <span data-ttu-id="432ce-262">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="432ce-262">UseCurrentThread</span></span>
- <span data-ttu-id="432ce-263">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="432ce-263">UseNewThread</span></span>

<span data-ttu-id="432ce-264">De standaard waarde is **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="432ce-264">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="432ce-265">Zie [PSThreadOptions Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.psthreadoptions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="432ce-265">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

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

### <span data-ttu-id="432ce-266">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="432ce-266">-TransportOption</span></span>

<span data-ttu-id="432ce-267">Hiermee geeft u de transport opties voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-267">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="432ce-268">Voer een transport opties-object in, zoals het **WSManConfigurationOption** -object dat de `New-PSTransportOption` cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="432ce-268">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="432ce-269">De opties voor sessies die gebruikmaken van de sessie configuratie, worden bepaald door de waarden van de sessie-opties en de opties voor sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-269">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="432ce-270">Tenzij opgegeven, hebben opties die in de sessie zijn ingesteld, zoals met behulp van de `New-PSSessionOption` cmdlet, voor rang boven de opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-270">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="432ce-271">De waarden van de sessie optie kunnen echter niet groter zijn dan de maximum waarden die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="432ce-271">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="432ce-272">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-272">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-273">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="432ce-273">-UseSharedProcess</span></span>

<span data-ttu-id="432ce-274">Gebruik slechts één proces om alle sessies te hosten die door dezelfde gebruiker zijn gestart en dezelfde sessie configuratie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="432ce-274">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="432ce-275">Standaard wordt elke sessie gehost in een eigen proces.</span><span class="sxs-lookup"><span data-stu-id="432ce-275">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="432ce-276">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-276">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="432ce-277">-Confirm</span><span class="sxs-lookup"><span data-stu-id="432ce-277">-Confirm</span></span>

<span data-ttu-id="432ce-278">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="432ce-278">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="432ce-279">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="432ce-279">-WhatIf</span></span>

<span data-ttu-id="432ce-280">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="432ce-280">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="432ce-281">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="432ce-281">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="432ce-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="432ce-282">CommonParameters</span></span>

<span data-ttu-id="432ce-283">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="432ce-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="432ce-284">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="432ce-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="432ce-285">INVOER</span><span class="sxs-lookup"><span data-stu-id="432ce-285">INPUTS</span></span>

### <span data-ttu-id="432ce-286">Geen</span><span class="sxs-lookup"><span data-stu-id="432ce-286">None</span></span>

<span data-ttu-id="432ce-287">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="432ce-287">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="432ce-288">UITVOER</span><span class="sxs-lookup"><span data-stu-id="432ce-288">OUTPUTS</span></span>

### <span data-ttu-id="432ce-289">Micro soft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="432ce-289">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="432ce-290">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="432ce-290">NOTES</span></span>

<span data-ttu-id="432ce-291">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="432ce-291">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="432ce-292">De `Set-PSSessionConfiguration` cmdlet heeft geen invloed op de configuratie naam en de **WSMan** -provider biedt geen ondersteuning voor de `Rename-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="432ce-292">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="432ce-293">Als u de naam van een sessie configuratie wilt wijzigen, gebruikt u de `Unregister-PSSessionConfiguration` cmdlet om de configuratie te verwijderen en gebruikt u vervolgens de `Register-PSSessionConfiguration` cmdlet om een nieuwe sessie configuratie te maken en te registreren.</span><span class="sxs-lookup"><span data-stu-id="432ce-293">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="432ce-294">U kunt de `Set-PSSessionConfiguration` cmdlet gebruiken om de standaard sessie configuraties van micro soft. Power shell en micro soft. PowerShell32 te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="432ce-294">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="432ce-295">Ze zijn niet beveiligd.</span><span class="sxs-lookup"><span data-stu-id="432ce-295">They are not protected.</span></span> <span data-ttu-id="432ce-296">Als u wilt terugkeren naar de oorspronkelijke versie van een standaard sessie configuratie, gebruikt u de `Unregister-PSSessionConfiguration` cmdlet om de standaard sessie configuratie te verwijderen en gebruikt u vervolgens de `Enable-PSRemoting` cmdlet om deze te herstellen.</span><span class="sxs-lookup"><span data-stu-id="432ce-296">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="432ce-297">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="432ce-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="432ce-298">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="432ce-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="432ce-299">U kunt opdrachten in WSMan: drive gebruiken om de eigenschappen van sessie configuraties te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="432ce-299">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="432ce-300">U kunt echter niet het WSMan:-station in Power Shell 2,0 gebruiken om de eigenschappen van de sessie configuratie te wijzigen die zijn geïntroduceerd in Power Shell 3,0, zoals **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="432ce-300">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="432ce-301">Windows Power Shell 2,0-opdrachten genereren geen fout, maar zijn niet effectief.</span><span class="sxs-lookup"><span data-stu-id="432ce-301">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="432ce-302">Als u eigenschappen wilt wijzigen die zijn geïntroduceerd in Power Shell 3,0, gebruikt u het station WSMan: in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="432ce-302">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="432ce-303">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="432ce-303">RELATED LINKS</span></span>

[<span data-ttu-id="432ce-304">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-304">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="432ce-305">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-305">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="432ce-306">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-306">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="432ce-307">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="432ce-307">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="432ce-308">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="432ce-308">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="432ce-309">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="432ce-309">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="432ce-310">New-New psworkflowexecutionoption</span><span class="sxs-lookup"><span data-stu-id="432ce-310">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="432ce-311">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-311">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="432ce-312">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-312">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="432ce-313">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="432ce-313">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="432ce-314">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="432ce-314">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="432ce-315">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="432ce-315">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="432ce-316">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="432ce-316">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="432ce-317">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="432ce-317">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
