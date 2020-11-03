---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 300fc3dee2e0d625e5aea42bfdcf45ea2e8b5a7f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251627"
---
# <span data-ttu-id="f105f-103">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-103">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="f105f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f105f-104">SYNOPSIS</span></span>
<span data-ttu-id="f105f-105">Hiermee worden de geregistreerde sessie configuraties op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f105f-105">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="f105f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f105f-106">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="f105f-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f105f-107">DESCRIPTION</span></span>

<span data-ttu-id="f105f-108">De `Get-PSSessionConfiguration` cmdlet haalt de sessie configuraties op die zijn geregistreerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-108">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="f105f-109">Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.</span><span class="sxs-lookup"><span data-stu-id="f105f-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="f105f-110">Vanaf Power Shell 3,0 kunt u de eigenschappen van een sessie configuratie definiëren met behulp van een sessie configuratie bestand (. pssc).</span><span class="sxs-lookup"><span data-stu-id="f105f-110">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="f105f-111">Met deze functie kunt u aangepaste en beperkte sessies maken zonder dat u een computer programma hoeft te schrijven.</span><span class="sxs-lookup"><span data-stu-id="f105f-111">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="f105f-112">Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="f105f-112">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="f105f-113">Daarnaast zijn er vanaf Power Shell 3,0 nieuwe notitie-eigenschappen toegevoegd aan het sessie configuratie object dat `Get-PSSessionConfiguration` retourneert.</span><span class="sxs-lookup"><span data-stu-id="f105f-113">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="f105f-114">Deze eigenschappen maken het gemakkelijker voor gebruikers en sessie configuratie ontwerpers om sessie configuraties te onderzoeken en vergelijken.</span><span class="sxs-lookup"><span data-stu-id="f105f-114">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="f105f-115">Als u een sessie configuratie wilt maken en registreren, gebruikt u de `Register-PSSessionConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f105f-115">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="f105f-116">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="f105f-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="f105f-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f105f-117">EXAMPLES</span></span>

### <span data-ttu-id="f105f-118">Voor beeld 1: sessie configuraties op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="f105f-118">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="f105f-119">Voor beeld 2: de twee standaard sessie configuraties ophalen</span><span class="sxs-lookup"><span data-stu-id="f105f-119">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="f105f-120">De opdracht gebruikt de para meter **name** van `Get-PSSessionConfiguration` om alleen de sessie configuraties op te halen met namen die beginnen met ' micro soft '.</span><span class="sxs-lookup"><span data-stu-id="f105f-120">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="f105f-121">Voor beeld 3: de eigenschappen en waarden van een sessie configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="f105f-121">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="f105f-122">In dit voor beeld worden de eigenschappen en eigenschaps waarden weer gegeven van een sessie configuratie die is gemaakt met behulp van een configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="f105f-122">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

<span data-ttu-id="f105f-123">In het voor beeld wordt de `Get-PSSessionConfiguration` cmdlet gebruikt om de volledige sessie configuratie op te halen.</span><span class="sxs-lookup"><span data-stu-id="f105f-123">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="f105f-124">Een pijplijn operator verzendt de volledige sessie configuratie naar de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f105f-124">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="f105f-125">Met de **eigenschaps** parameter met de waarde `*` (all) `Format-List` worden alle eigenschappen en waarden van het object in een lijst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f105f-125">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="f105f-126">De uitvoer bevat nuttige informatie, waaronder de auteur van de sessie configuratie, het sessie type, de taal modus en het uitvoerings beleid van sessies die zijn gemaakt met deze sessie configuratie, sessie quota en het volledige pad naar het sessie configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="f105f-126">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="f105f-127">Deze weer gave van een sessie configuratie wordt gebruikt voor sessies die een sessie configuratie bestand bevatten.</span><span class="sxs-lookup"><span data-stu-id="f105f-127">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="f105f-128">Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="f105f-128">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="f105f-129">Voor beeld 4: een andere manier om de sessie configuraties te bekijken</span><span class="sxs-lookup"><span data-stu-id="f105f-129">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="f105f-130">In dit voor beeld wordt de `Get-ChildItem` cmdlet (alias `dir` ) in het station WSMan: provider gebruikt om de inhoud van het knoop punt van de invoeg toepassing te bekijken.</span><span class="sxs-lookup"><span data-stu-id="f105f-130">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="f105f-131">Dit is een andere manier om de sessie configuraties op de computer te bekijken.</span><span class="sxs-lookup"><span data-stu-id="f105f-131">This is another way to look at the session configurations on the computer.</span></span>

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="f105f-132">Het knoop punt van de **invoeg toepassing** bevat **ContainerElement** -objecten (micro soft. WSMan. Management. WSManConfigContainerElement) die de geregistreerde Power shell-sessie configuraties vertegenwoordigen, samen met andere invoeg toepassingen voor WS-Management.</span><span class="sxs-lookup"><span data-stu-id="f105f-132">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="f105f-133">Voor beeld 6: sessie configuraties op een externe computer weer geven</span><span class="sxs-lookup"><span data-stu-id="f105f-133">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="f105f-134">In dit voor beeld ziet u hoe u de WSMan-provider kunt gebruiken om de sessie configuraties op een externe computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f105f-134">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="f105f-135">Deze methode biedt niet zoveel informatie als een `Get-PSSessionConfiguration` opdracht, maar de gebruiker hoeft geen lid te zijn van de groep Administrators om deze cmdlet uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f105f-135">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="f105f-136">De `Connect-WSMan` cmdlet maakt verbinding met de WinRM-service op de externe Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-136">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="f105f-137">De `Get-ChildItem` cmdlet (alias `dir` ) van het WSMan: station haalt de items op in het pad **Server01\Plugin** .</span><span class="sxs-lookup"><span data-stu-id="f105f-137">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="f105f-138">In de uitvoer ziet u de items in de map voor de invoeg toepassing op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="f105f-138">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="f105f-139">De items omvatten de sessie configuraties, die een type WSMan-invoeg toepassing zijn, samen met andere typen invoeg toepassingen op de computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-139">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="f105f-140">Voor beeld 7: gedetailleerde sessie configuraties van een externe computer ophalen</span><span class="sxs-lookup"><span data-stu-id="f105f-140">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="f105f-141">In dit voor beeld ziet u hoe u een `Get-PSSessionConfiguration` opdracht op een externe computer uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f105f-141">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="f105f-142">Voor de opdracht is vereist dat CredSSP delegering is ingeschakeld in de client instellingen op de lokale computer en in de service-instellingen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-142">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="f105f-143">Als u de opdrachten in dit voor beeld wilt uitvoeren, moet u lid zijn van de groep Administrators op de lokale en externe computers en moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="f105f-143">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

<span data-ttu-id="f105f-144">`Enable-WSManCredSSP`Met de cmdlet schakelt u **CredSSP** -delegering in op Server01, de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-144">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="f105f-145">De `Connect-WSMan` cmdlet maakt verbinding met de Server02-computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-145">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="f105f-146">Met deze actie wordt een knoop punt voor Server02 toegevoegd aan het WSMan:-station op de lokale computer, zodat u de WS-Management instellingen op de Server02-computer kunt weer geven en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f105f-146">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="f105f-147">Met de `Set-Item` cmdlet wordt de waarde van het **CredSSP** -item in het knoop punt service van de Server02-computer gewijzigd in **True**.</span><span class="sxs-lookup"><span data-stu-id="f105f-147">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True**.</span></span> <span data-ttu-id="f105f-148">Hiermee configureert u de service-instellingen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-148">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="f105f-149">De `Invoke-Command` cmdlet voert de `Get-PSSessionConfiguration` opdracht uit op de Server02-computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-149">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="f105f-150">De opdracht gebruikt de para meter **Credential** en gebruikt de **verificatie** parameter met de waarde **CredSSP**.</span><span class="sxs-lookup"><span data-stu-id="f105f-150">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP**.</span></span> <span data-ttu-id="f105f-151">In de uitvoer ziet u de sessie configuraties op de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="f105f-151">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="f105f-152">Voor beeld 8: de bron-URI van een sessie configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="f105f-152">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="f105f-153">Dit voor beeld is handig voor het instellen van de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele, die een resource-URI gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f105f-153">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="f105f-154">De `$PSSessionConfigurationName` variabele geeft de standaard configuratie op die wordt gebruikt bij het maken van een sessie.</span><span class="sxs-lookup"><span data-stu-id="f105f-154">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="f105f-155">Deze variabele is ingesteld op de lokale computer, maar Hiermee wordt een configuratie op de externe computer opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f105f-155">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="f105f-156">Zie about_Preference_Variables voor meer informatie over de `$PSSessionConfiguration` variabele [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f105f-156">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="f105f-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f105f-157">PARAMETERS</span></span>

### <span data-ttu-id="f105f-158">-Force</span><span class="sxs-lookup"><span data-stu-id="f105f-158">-Force</span></span>

<span data-ttu-id="f105f-159">Onderdrukt de prompt om de WinRM-service opnieuw te starten als de service nog niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f105f-159">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="f105f-160">-Name</span><span class="sxs-lookup"><span data-stu-id="f105f-160">-Name</span></span>

<span data-ttu-id="f105f-161">Hiermee worden alleen de sessie configuraties met het opgegeven naam-of naam patroon opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f105f-161">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="f105f-162">Voer een of meer sessie configuratie namen in.</span><span class="sxs-lookup"><span data-stu-id="f105f-162">Enter one or more session configuration names.</span></span> <span data-ttu-id="f105f-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f105f-163">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f105f-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f105f-164">CommonParameters</span></span>

<span data-ttu-id="f105f-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f105f-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f105f-166">Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f105f-166">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f105f-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="f105f-167">INPUTS</span></span>

### <span data-ttu-id="f105f-168">Geen</span><span class="sxs-lookup"><span data-stu-id="f105f-168">None</span></span>

<span data-ttu-id="f105f-169">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f105f-169">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f105f-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f105f-170">OUTPUTS</span></span>

### <span data-ttu-id="f105f-171">Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="f105f-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f105f-172">NOTES</span></span>

- <span data-ttu-id="f105f-173">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="f105f-173">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="f105f-174">Als u de sessie configuraties op de computer wilt weer geven, moet u lid zijn van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-174">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="f105f-175">Als u een `Get-PSSessionConfiguration` opdracht op een externe computer wilt uitvoeren, moet de CredSSP-verificatie (Credential Security service provider) zijn ingeschakeld in de client instellingen op de lokale computer (met behulp van de `Enable-WSManCredSSP` cmdlet) en in de service-instellingen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f105f-175">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="f105f-176">U moet ook de **CredSSP** -waarde van de **verificatie** parameter gebruiken bij het tot stand brengen van de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f105f-176">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="f105f-177">Anders wordt de toegang geweigerd.</span><span class="sxs-lookup"><span data-stu-id="f105f-177">Otherwise, access is denied.</span></span>

- <span data-ttu-id="f105f-178">De notitie-eigenschappen van het object die `Get-PSSessionConfiguration` worden geretourneerd, worden alleen weer gegeven op het object wanneer ze een waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="f105f-178">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="f105f-179">Alleen sessie configuraties die zijn gemaakt met behulp van een sessie configuratie bestand hebben alle gedefinieerde eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="f105f-179">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="f105f-180">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="f105f-180">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="f105f-181">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="f105f-181">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="f105f-182">U kunt opdrachten in WSMan: drive gebruiken om de eigenschappen van sessie configuraties te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f105f-182">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="f105f-183">U kunt echter niet het WSMan:-station in Power Shell 2,0 gebruiken om de eigenschappen van de sessie configuratie te wijzigen die zijn geïntroduceerd in Power Shell 3,0, zoals **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="f105f-183">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="f105f-184">Power Shell 2,0-opdrachten genereren geen fout, maar zijn niet effectief.</span><span class="sxs-lookup"><span data-stu-id="f105f-184">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="f105f-185">Als u eigenschappen wilt wijzigen die zijn geïntroduceerd in Power Shell 3,0, gebruikt u het station WSMan: in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f105f-185">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="f105f-186">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f105f-186">RELATED LINKS</span></span>

[<span data-ttu-id="f105f-187">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-187">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="f105f-188">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-188">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="f105f-189">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-189">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="f105f-190">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f105f-190">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="f105f-191">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="f105f-191">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="f105f-192">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-192">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="f105f-193">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-193">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="f105f-194">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f105f-194">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="f105f-195">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f105f-195">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="f105f-196">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="f105f-196">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="f105f-197">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="f105f-197">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="f105f-198">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="f105f-198">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

