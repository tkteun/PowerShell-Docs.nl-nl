---
description: Hierin worden de configuratie bestanden voor de sessie beschreven, die worden gebruikt in een sessie configuratie (ook wel een ' eind punt ' genoemd) om de omgeving van sessies te definiëren die gebruikmaken van de sessie configuratie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 45c8a6e0ba8478e0a49cb287cd4311d7556a42ea
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252139"
---
# <a name="about-session-configuration-files"></a><span data-ttu-id="57d89-104">Over sessie configuratie bestanden</span><span class="sxs-lookup"><span data-stu-id="57d89-104">About Session Configuration Files</span></span>

## <a name="short-description"></a><span data-ttu-id="57d89-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="57d89-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="57d89-106">Hierin worden de configuratie bestanden voor de sessie beschreven, die worden gebruikt in een sessie configuratie (ook wel een ' eind punt ' genoemd) om de omgeving van sessies te definiëren die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-106">Describes session configuration files, which are used in a session configuration (also known as an "endpoint") to define the environment of sessions that use the session configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="57d89-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="57d89-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="57d89-108">Een ' sessie configuratie bestand ' is een tekst bestand met de bestandsnaam extensie. pssc dat een hashtabel bevat van de eigenschappen en waarden van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-108">A "session configuration file" is a text file with a .pssc file name extension that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="57d89-109">U kunt een sessie configuratie bestand gebruiken om de eigenschappen van een sessie configuratie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="57d89-109">You can use a session configuration file to set the properties of a session configuration.</span></span> <span data-ttu-id="57d89-110">Hiermee definieert u de omgeving van elke Power shell-sessie die deze sessie configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="57d89-110">Doing so defines the environment of any PowerShell sessions that use that session configuration.</span></span>

<span data-ttu-id="57d89-111">Met sessie configuratie bestanden kunt u eenvoudig aangepaste sessie configuraties maken zonder ingewikkelde C#-assembly's of-scripts te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57d89-111">Session configuration files make it easy to create custom session configurations without using complex C# assemblies or scripts.</span></span>

<span data-ttu-id="57d89-112">Een ' sessie configuratie ' of ' eind punt ' is een verzameling lokale computer instellingen die de dingen bepalen waarmee gebruikers sessies op de computer kunnen maken. welke opdrachten gebruikers in deze sessies kunnen uitvoeren; en of de sessie moet worden uitgevoerd als een privileged virtueel account.</span><span class="sxs-lookup"><span data-stu-id="57d89-112">A "session configuration" or "endpoint" is a collection of local computer settings that determine such things as which users can create sessions on the computer; which commands users can run in those sessions; and whether the session should run as a privileged virtual account.</span></span> <span data-ttu-id="57d89-113">Zie [about_Session_Configurations](about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="57d89-113">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

<span data-ttu-id="57d89-114">Er zijn sessie configuraties geïntroduceerd in Windows Power Shell 2,0 en sessie configuratie bestanden zijn geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="57d89-114">Session configurations were introduced in Windows PowerShell 2.0, and session configuration files were introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="57d89-115">U moet Windows Power Shell 3,0 gebruiken voor het toevoegen van een sessie configuratie bestand in een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-115">You must use Windows PowerShell 3.0 to include a session configuration file in a session configuration.</span></span> <span data-ttu-id="57d89-116">Gebruikers van Windows Power Shell 2,0 (en hoger) worden echter beïnvloed door de instellingen in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-116">However, users of Windows PowerShell 2.0 (and later) are affected by the settings in the session configuration.</span></span>

## <a name="creating-custom-sessions"></a><span data-ttu-id="57d89-117">Aangepaste sessies maken</span><span class="sxs-lookup"><span data-stu-id="57d89-117">Creating Custom Sessions</span></span>

<span data-ttu-id="57d89-118">U kunt een groot aantal functies van een Power shell-sessie aanpassen door sessie-eigenschappen in een sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="57d89-118">You can customize many features of a PowerShell session by specifying session properties in a session configuration.</span></span> <span data-ttu-id="57d89-119">U kunt een sessie aanpassen door een C#-programma te schrijven dat een aangepaste runs Pace definieert, of u kunt een sessie configuratie bestand gebruiken om de eigenschappen te definiëren van sessies die zijn gemaakt met behulp van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-119">You can customize a session by writing a C# program that defines a custom runspace, or you can use a session configuration file to define the properties of sessions created by using the session configuration.</span></span> <span data-ttu-id="57d89-120">In het algemeen is het eenvoudiger om het sessie configuratie bestand te gebruiken dan om een C#-programma te schrijven.</span><span class="sxs-lookup"><span data-stu-id="57d89-120">As a general rule, it is easier to use the session configuration file than to write a C# program.</span></span>

<span data-ttu-id="57d89-121">U kunt een sessie configuratie bestand gebruiken om items te maken, zoals volledig werkende sessies voor zeer vertrouwde gebruikers. vergrendelde sessies die minimale toegang toestaan; sessies die zijn ontworpen met name en die alleen de modules bevatten die nodig zijn voor deze taken; en sessies waarbij niet-gemachtigde gebruikers alleen specifieke opdrachten kunnen uitvoeren als een bevoegd account.</span><span class="sxs-lookup"><span data-stu-id="57d89-121">You can use a session configuration file to create items such as fully-functioning sessions for highly trusted users; locked-down sessions that allow minimal access; sessions designed for particular and that contain only the modules required for those tasks; and sessions where unprivileged users can only run specific commands as a privileged account.</span></span>

<span data-ttu-id="57d89-122">Daarnaast kunt u beheren of gebruikers van de sessie Power shell-taal elementen zoals script blokken kunnen gebruiken, of dat ze alleen opdrachten kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="57d89-122">In addition to that, you can manage whether users of the session can use PowerShell language elements such as script blocks, or whether they can only run commands.</span></span> <span data-ttu-id="57d89-123">U kunt de versie van Power shell-gebruikers beheren in de sessie. beheren welke modules in de sessie worden geïmporteerd; en beheren welke cmdlets, functies en aliassen sessie gebruikers kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="57d89-123">You can manage the version of PowerShell users can run in the session; manage which modules are imported into the session; and manage which cmdlets, functions, and aliases session users can run.</span></span> <span data-ttu-id="57d89-124">Wanneer u het veld RoleDefinitions gebruikt, kunt u gebruikers verschillende mogelijkheden geven in de sessie op basis van groepslid maatschap.</span><span class="sxs-lookup"><span data-stu-id="57d89-124">When using the RoleDefinitions field, you can give users different capabilities in the session based on group membership.</span></span>

<span data-ttu-id="57d89-125">Zie het Help-onderwerp voor de cmdlet New-PSRoleCapabilityFile voor meer informatie over RoleDefinitions en het definiëren van deze waarde.</span><span class="sxs-lookup"><span data-stu-id="57d89-125">For more information about RoleDefinitions and how to define this Value, see the help topic for the New-PSRoleCapabilityFile Cmdlet.</span></span>

## <a name="creating-a-session-configuration-file"></a><span data-ttu-id="57d89-126">Een configuratie bestand voor de sessie maken</span><span class="sxs-lookup"><span data-stu-id="57d89-126">Creating a Session Configuration File</span></span>

<span data-ttu-id="57d89-127">De eenvoudigste manier om een sessie configuratie bestand te maken, is met behulp van de cmdlet New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="57d89-127">The easiest way to create a session configuration file is by using the New-PSSessionConfigurationFile cmdlet.</span></span> <span data-ttu-id="57d89-128">Met deze cmdlet wordt een bestand gegenereerd dat gebruikmaakt van de juiste syntaxis en indeling en dat veel eigenschaps waarden van het configuratie bestand automatisch verifieert.</span><span class="sxs-lookup"><span data-stu-id="57d89-128">This cmdlet generates a file that uses the correct syntax and format, and that automatically verifies many of the configuration file property values.</span></span>

<span data-ttu-id="57d89-129">Zie het Help-onderwerp voor de cmdlet New-PSSessionConfigurationFile voor gedetailleerde beschrijvingen van de eigenschappen die u in een sessie configuratie bestand kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="57d89-129">For detailed descriptions of the properties that you can set in a session configuration file, see the help topic for the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="57d89-130">Met de volgende opdracht maakt u een sessie configuratie bestand dat gebruikmaakt van de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="57d89-130">The following command creates a session configuration file that uses the default values.</span></span> <span data-ttu-id="57d89-131">In het resulterende configuratie bestand worden alleen de standaard waarden gebruikt omdat er geen para meters zijn met uitzonde ring van de para meter Path (waarmee het bestandspad wordt opgegeven):</span><span class="sxs-lookup"><span data-stu-id="57d89-131">The resulting configuration file uses only the default values because no parameters other than the Path parameter (which specifies the file path) are included:</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

<span data-ttu-id="57d89-132">Als u het nieuwe configuratie bestand in de standaard tekst editor wilt weer geven, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="57d89-132">To view the new configuration file in your default text editor, use the following command:</span></span>

```powershell
Invoke-Item -Path .\Defaults.pssc
```

<span data-ttu-id="57d89-133">Als u een sessie configuratie wilt maken voor sessies waarin de gebruiker opdrachten kan uitvoeren, maar geen andere elementen van de Power shell-taal, typt u:</span><span class="sxs-lookup"><span data-stu-id="57d89-133">To create a session configuration for sessions in which user can run commands, but not use other elements of the PowerShell language, type:</span></span>

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="57d89-134">In de voor gaande opdracht stelt u de para meter LanguageMode in op geen taal, voor komt u dat gebruikers dingen doen als schrijven of uitvoeren van scripts of met behulp van variabelen.</span><span class="sxs-lookup"><span data-stu-id="57d89-134">In the preceding command, setting the LanguageMode parameter to NoLanguage prevents users from doing such things as writing or running scripts, or using variables.</span></span>

<span data-ttu-id="57d89-135">Voor het maken van een sessie configuratie voor sessies waarin gebruikers alleen cmdlets kunnen gebruiken, typt u:</span><span class="sxs-lookup"><span data-stu-id="57d89-135">To create a session configuration for sessions in which users can use only Get cmdlets, type:</span></span>

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

<span data-ttu-id="57d89-136">In het vorige voor beeld stelt u de para meter VisibleCmdlets in op Get-\* om gebruikers te beperken tot cmdlets met een naam die begint met de teken reeks waarde ' Get-'.</span><span class="sxs-lookup"><span data-stu-id="57d89-136">In the preceding example, setting the VisibleCmdlets parameter to Get-\* limits users to cmdlets that have names that start with the string value "Get-".</span></span>

<span data-ttu-id="57d89-137">Als u een sessie configuratie wilt maken voor sessies die worden uitgevoerd onder een privileged Virtual account in plaats van de referenties van de gebruiker, typt u:</span><span class="sxs-lookup"><span data-stu-id="57d89-137">To create a session configuration for sessions that run under a privileged virtual account instead of the user's credentials, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

<span data-ttu-id="57d89-138">Als u een sessie configuratie wilt maken voor sessies waarin de opdrachten die zichtbaar zijn voor de gebruiker worden opgegeven in een bestand met functie mogelijkheden, typt u:</span><span class="sxs-lookup"><span data-stu-id="57d89-138">To create a session configuration for sessions in which the commands visible to the user are specified in a role capabilities file, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a><span data-ttu-id="57d89-139">Een sessie configuratie bestand gebruiken</span><span class="sxs-lookup"><span data-stu-id="57d89-139">Using a Session Configuration File</span></span>

<span data-ttu-id="57d89-140">U kunt een sessie configuratie bestand toevoegen wanneer u een sessie configuratie maakt of toevoegt. u kunt een bestand op een later tijdstip toevoegen aan de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-140">You can include a session configuration file when you create a session configuration or add you can add a file to the session configuration at a later time.</span></span>

<span data-ttu-id="57d89-141">Als u een sessie configuratie bestand wilt toevoegen bij het maken van een sessie configuratie, gebruikt u de para meter Path van de cmdlet Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="57d89-141">To include a session configuration file when creating a session configuration, use the Path parameter of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="57d89-142">Met de volgende opdracht wordt bijvoorbeeld het bestand pssc gebruikt wanneer er een configuratie voor een niet-getaalde sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="57d89-142">For example, the following command uses the NoLanguage.pssc file when it creates a NoLanguage session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="57d89-143">Wanneer een nieuwe niet-taal sessie wordt gestart, hebben gebruikers alleen toegang tot Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="57d89-143">When a new NoLanguage session starts, users will only have access to PowerShell commands.</span></span>

<span data-ttu-id="57d89-144">Als u een sessie configuratie bestand wilt toevoegen aan een bestaande sessie configuratie, gebruikt u de cmdlet Set-PSSessionConfiguration en de para meter Path.</span><span class="sxs-lookup"><span data-stu-id="57d89-144">To add a session configuration file to an existing session configuration, use the Set-PSSessionConfiguration cmdlet and the Path parameter.</span></span> <span data-ttu-id="57d89-145">Dit is van invloed op nieuwe sessies die zijn gemaakt met de opgegeven sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-145">This affects any new sessions created with the specified session configuration.</span></span> <span data-ttu-id="57d89-146">Houd er rekening mee dat de cmdlet Set-PSSessionConfiguration de sessie zelf wijzigt en het sessie configuratie bestand niet wijzigt.</span><span class="sxs-lookup"><span data-stu-id="57d89-146">Note that the Set-PSSessionConfiguration cmdlet changes the session itself and does not modify the session configuration file.</span></span>

<span data-ttu-id="57d89-147">Met de volgende opdracht wordt bijvoorbeeld het bestand ' pssc ' toegevoegd aan de configuratie van de LockedDown-sessie.</span><span class="sxs-lookup"><span data-stu-id="57d89-147">For example, the following command adds the NoLanguage.pssc file to the LockedDown session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

<span data-ttu-id="57d89-148">Wanneer gebruikers de configuratie van de LockedDown-sessie gebruiken om een sessie te maken, kunnen ze cmdlets uitvoeren, maar ze kunnen geen variabelen maken of gebruiken, waarden toewijzen of andere Power shell-taal elementen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57d89-148">When users use the LockedDown session configuration to create a session, they will be able to run cmdlets but they will not be able to create or use variables, assign values, or use other PowerShell language elements.</span></span>

<span data-ttu-id="57d89-149">De volgende opdracht maakt gebruik van de New-PSSession cmdlet om een sessie te maken op de computer Srv01 die gebruikmaakt van de configuratie van de LockedDown-sessie, waarbij een object verwijzing naar de sessie in de $s variabele wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="57d89-149">The following command uses the New-PSSession cmdlet to create a session on the computer Srv01 that uses the LockedDown session configuration, saving an object reference to the session in the $s variable.</span></span> <span data-ttu-id="57d89-150">De ACL (toegangs beheer lijst) van de sessie configuratie bepaalt wie deze kan gebruiken om een sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="57d89-150">The ACL (access control list) of the session configuration determines who can use it to create a session.</span></span>

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

<span data-ttu-id="57d89-151">Omdat de niet-taal beperkingen zijn toegevoegd aan de LockedDown-sessie configuratie, kunnen gebruikers in LockedDown-sessies alleen Power shell-opdrachten en-cmdlets uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="57d89-151">Because the NoLanguage constraints were added to the LockedDown session configuration, users in LockedDown sessions will only be able to run PowerShell commands and cmdlets.</span></span> <span data-ttu-id="57d89-152">De volgende twee opdrachten gebruiken bijvoorbeeld de cmdlet Invoke-Command om opdrachten uit te voeren in de sessie waarnaar wordt verwezen in de $s-variabele.</span><span class="sxs-lookup"><span data-stu-id="57d89-152">For example, the following two commands use the Invoke-Command cmdlet to run commands in the session referenced in the $s variable.</span></span> <span data-ttu-id="57d89-153">De eerste opdracht, waarmee de cmdlet Get-UICulture wordt uitgevoerd en geen variabelen gebruikt, slaagt.</span><span class="sxs-lookup"><span data-stu-id="57d89-153">The first command, which runs the Get-UICulture cmdlet and does not use any variables, succeeds.</span></span> <span data-ttu-id="57d89-154">De tweede opdracht, waarmee de waarde van de variabele $PSUICulture wordt opgehaald, mislukt.</span><span class="sxs-lookup"><span data-stu-id="57d89-154">The second command, which gets the value of the $PSUICulture variable, fails.</span></span>

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a><span data-ttu-id="57d89-155">Een sessie configuratie bestand bewerken</span><span class="sxs-lookup"><span data-stu-id="57d89-155">Editing a Session Configuration File</span></span>

<span data-ttu-id="57d89-156">Alle instellingen in een sessie configuratie, met uitzonde ring van RunAsVirtualAccount en RunAsVirtualAccountGroups, kunnen worden gewijzigd door het sessie configuratie bestand te bewerken dat door de sessie configuratie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="57d89-156">All settings in a session configuration except for RunAsVirtualAccount and RunAsVirtualAccountGroups can be modified by editing the session configuration file used by the session configuration.</span></span> <span data-ttu-id="57d89-157">Om dit te doen, moet u eerst de actieve kopie van het sessie configuratie bestand zoeken.</span><span class="sxs-lookup"><span data-stu-id="57d89-157">To do this, begin by locating the active copy of the session configuration file.</span></span>

<span data-ttu-id="57d89-158">Wanneer u een sessie configuratie bestand in een sessie configuratie gebruikt, maakt Power shell een actieve kopie van het sessie configuratie bestand en slaat deze op in de \$ \\ map pshome SessionConfig op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="57d89-158">When you use a session configuration file in a session configuration, PowerShell creates an active copy of the session configuration file and stores it in the \$pshome\\SessionConfig directory on the local computer.</span></span>

<span data-ttu-id="57d89-159">De locatie van de actieve kopie van een sessie configuratie bestand wordt opgeslagen in de eigenschap ConfigFilePath van het object voor sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-159">The location of the active copy of a session configuration file is stored in the ConfigFilePath property of the session configuration object.</span></span>

<span data-ttu-id="57d89-160">Met de volgende opdracht wordt de locatie van het sessie configuratie bestand voor de configuratie van de niet-getaalde sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="57d89-160">The following command gets the location of the session configuration file for the NoLanguage session configuration.</span></span>

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

<span data-ttu-id="57d89-161">Met deze opdracht wordt een bestandspad geretourneerd dat er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="57d89-161">That command returns a file path similar to the following:</span></span>

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="57d89-162">U kunt het. pssc-bestand bewerken in een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="57d89-162">You can edit the .pssc file in any text editor.</span></span> <span data-ttu-id="57d89-163">Nadat het bestand is opgeslagen, wordt het gebruikt door alle nieuwe sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-163">After the file is saved it will be employed by any new sessions that use the session configuration.</span></span>

<span data-ttu-id="57d89-164">Als u de instellingen voor RunAsVirtualAccount of RunAsVirtualAccountGroups moet wijzigen, moet u de registratie van de sessie configuratie ongedaan maken en een sessie configuratie bestand dat de bewerkte waarden bevat, opnieuw registreren.</span><span class="sxs-lookup"><span data-stu-id="57d89-164">If you need to modify the RunAsVirtualAccount or the RunAsVirtualAccountGroups settings, you must un-register the session configuration and re-register a session configuration file that includes the edited values.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="57d89-165">Een configuratie bestand voor een sessie testen</span><span class="sxs-lookup"><span data-stu-id="57d89-165">Testing a Session Configuration File</span></span>

<span data-ttu-id="57d89-166">Gebruik de cmdlet Test-PSSessionConfigurationFile om hand matig bewerkte sessie configuratie bestanden te testen.</span><span class="sxs-lookup"><span data-stu-id="57d89-166">Use the Test-PSSessionConfigurationFile cmdlet to test manually edited session configuration files.</span></span> <span data-ttu-id="57d89-167">Dat is belang rijk: als de syntaxis en waarden van het bestand niet geldig zijn, kunnen gebruikers de sessie configuratie niet gebruiken om een sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="57d89-167">That's important: if the file syntax and values are not valid users will not be able to use the session configuration to create a session.</span></span>

<span data-ttu-id="57d89-168">Met de volgende opdracht wordt bijvoorbeeld het configuratie bestand van de actieve sessie van de configuratie van de niet-taal sessie getest.</span><span class="sxs-lookup"><span data-stu-id="57d89-168">For example, the following command tests the active session configuration file of the NoLanguage session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="57d89-169">Als de syntaxis en waarden in het configuratie bestand geldig zijn Test-PSSessionConfigurationFile retourneert True.</span><span class="sxs-lookup"><span data-stu-id="57d89-169">If the syntax and values in the configuration file are valid Test-PSSessionConfigurationFile returns True.</span></span> <span data-ttu-id="57d89-170">Als de syntaxis en waarden niet geldig zijn, retourneert de cmdlet false.</span><span class="sxs-lookup"><span data-stu-id="57d89-170">If the syntax and values are not valid then the cmdlet returns False.</span></span>

<span data-ttu-id="57d89-171">U kunt Test-PSSessionConfigurationFile gebruiken om een sessie configuratie bestand te testen, inclusief bestanden die door de New-PSSessionConfiguration-cmdlet worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="57d89-171">You can use Test-PSSessionConfigurationFile to test any session configuration file, including files that the New-PSSessionConfiguration cmdlet creates.</span></span> <span data-ttu-id="57d89-172">Zie het Help-onderwerp voor de cmdlet Test-PSSessionConfigurationFile voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="57d89-172">For more information, see the help topic for the Test-PSSessionConfigurationFile cmdlet.</span></span>

## <a name="removing-a-session-configuration-file"></a><span data-ttu-id="57d89-173">Een sessie configuratie bestand verwijderen</span><span class="sxs-lookup"><span data-stu-id="57d89-173">Removing a Session Configuration File</span></span>

<span data-ttu-id="57d89-174">U kunt een sessie configuratie bestand niet verwijderen uit een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-174">You cannot remove a session configuration file from a session configuration.</span></span>
<span data-ttu-id="57d89-175">U kunt het bestand echter vervangen door een nieuw bestand dat de standaard instellingen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="57d89-175">However, you can replace the file with a new file that uses the default settings.</span></span> <span data-ttu-id="57d89-176">Hiermee worden de instellingen die worden gebruikt door het oorspronkelijke configuratie bestand in feite geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="57d89-176">This effectively cancels the settings used by the original configuration file.</span></span>

<span data-ttu-id="57d89-177">Als u een configuratie bestand voor de sessie wilt vervangen, maakt u een nieuw sessie configuratie bestand dat gebruikmaakt van de standaard instellingen en gebruikt u vervolgens de cmdlet Set-PSSessionConfiguration om het aangepaste sessie configuratie bestand te vervangen door het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="57d89-177">To replace a session configuration file, create a new session configuration file that uses the default settings, then use the Set-PSSessionConfiguration cmdlet to replace the custom session configuration file with the new file.</span></span>

<span data-ttu-id="57d89-178">Met de volgende opdrachten maakt u bijvoorbeeld een standaard sessie configuratie bestand en vervangt u vervolgens het configuratie bestand van de actieve sessie in de configuratie van de niet-taal sessie.</span><span class="sxs-lookup"><span data-stu-id="57d89-178">For example, the following commands create a Default session configuration file and then replace the active session configuration file in the NoLanguage session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

<span data-ttu-id="57d89-179">Als deze opdrachten zijn voltooid, biedt de configuratie van de sessie zonder taal de volledige taal ondersteuning (de standaard instelling) voor alle sessies die zijn gemaakt met die sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="57d89-179">When these commands finish, the NoLanguage session configuration will actually provide full language support (the default setting) for all sessions created with that session configuration.</span></span>

<span data-ttu-id="57d89-180">Het weer geven van de eigenschappen van een sessie configuratie de sessie configuratie objecten die sessie configuraties vertegenwoordigen met behulp van sessie configuratie bestanden hebben extra eigenschappen waarmee u de sessie configuratie eenvoudig kunt detecteren en analyseren.</span><span class="sxs-lookup"><span data-stu-id="57d89-180">Viewing the Properties of a Session Configuration The session configuration objects that represent session configurations using session configuration files have additional properties that make it easy to discover and analyze the session configuration.</span></span> <span data-ttu-id="57d89-181">(Houd er rekening mee dat de hieronder weer gegeven type naam een opmaak definitie bevat.) U kunt de eigenschappen weer geven door de Get-PSSessionConfiguration-cmdlet uit te voeren en de geretourneerde gegevens te sluizen naar de Get-Member-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="57d89-181">(Note that the type name shown below includes a formatted view definition.) You can view the properties by running the Get-PSSessionConfiguration cmdlet and piping the returned data to the Get-Member cmdlet:</span></span>

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

<span data-ttu-id="57d89-182">Met deze eigenschappen kunt u eenvoudig zoeken naar specifieke sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="57d89-182">These properties make it easy to search for specific session configurations.</span></span>
<span data-ttu-id="57d89-183">U kunt bijvoorbeeld de eigenschap ExecutionPolicy gebruiken om een sessie configuratie te vinden die ondersteuning biedt voor sessies met het beleid voor het uitvoeren van RemoteSigned.</span><span class="sxs-lookup"><span data-stu-id="57d89-183">For example, you can use the ExecutionPolicy property to find a session configuration that supports sessions with the RemoteSigned execution policy.</span></span>
<span data-ttu-id="57d89-184">Houd er rekening mee dat, omdat de eigenschap ExecutionPolicy alleen bestaat voor sessies die gebruikmaken van sessie configuratie bestanden, de opdracht mogelijk niet alle in aanmerking komende sessie configuraties retourneert.</span><span class="sxs-lookup"><span data-stu-id="57d89-184">Note that, because the ExecutionPolicy property exists only on sessions that use session configuration files, the command might not return all qualifying session configurations.</span></span>

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

<span data-ttu-id="57d89-185">Met de volgende opdracht worden de sessie configuraties opgehaald waarin de RunAsUser de Exchange-beheerder is.</span><span class="sxs-lookup"><span data-stu-id="57d89-185">The following command gets session configurations in which the RunAsUser is the Exchange administrator.</span></span>

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

<span data-ttu-id="57d89-186">Gebruik de cmdlet Get-PSSessionCapability om informatie weer te geven over de roldefinities die aan een configuratie zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="57d89-186">To view information about the role definitions associated with a configuration use the Get-PSSessionCapability cmdlet.</span></span> <span data-ttu-id="57d89-187">Met deze cmdlet kunt u de opdrachten en omgeving bepalen die beschikbaar zijn voor specifieke gebruikers in specifieke eind punten.</span><span class="sxs-lookup"><span data-stu-id="57d89-187">This cmdlet enables you to determine the commands and environment available to specific users in specific endpoints.</span></span>

## <a name="notes"></a><span data-ttu-id="57d89-188">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="57d89-188">NOTES</span></span>

<span data-ttu-id="57d89-189">Sessie configuraties bieden ook ondersteuning voor een type sessie dat een ' lege ' sessie wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="57d89-189">Session configurations also support a type of session known as an "empty" session.</span></span> <span data-ttu-id="57d89-190">Met een leeg sessie type kunt u aangepaste sessies maken met geselecteerde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="57d89-190">An Empty session type enables you to create custom sessions with selected commands.</span></span> <span data-ttu-id="57d89-191">Als u geen modules, functies of scripts aan een lege sessie toevoegt, is de sessie beperkt tot expressies en is deze mogelijk niet van praktisch gebruik.</span><span class="sxs-lookup"><span data-stu-id="57d89-191">If you do not add modules, functions, or scripts to an empty session, the session is limited to expressions and might not be of any practical use.</span></span> <span data-ttu-id="57d89-192">De eigenschap SessionType vertelt u of u met een lege sessie werkt.</span><span class="sxs-lookup"><span data-stu-id="57d89-192">The SessionType property tells you whether or not you are working with an empty session.</span></span>

## <a name="see-also"></a><span data-ttu-id="57d89-193">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="57d89-193">SEE ALSO</span></span>

[<span data-ttu-id="57d89-194">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="57d89-194">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="57d89-195">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="57d89-195">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="57d89-196">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d89-196">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="57d89-197">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d89-197">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="57d89-198">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d89-198">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="57d89-199">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="57d89-199">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="57d89-200">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d89-200">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="57d89-201">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d89-201">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="57d89-202">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="57d89-202">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="57d89-203">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d89-203">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[<span data-ttu-id="57d89-204">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="57d89-204">Get-PSSessionCapability</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[<span data-ttu-id="57d89-205">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="57d89-205">New-PSRoleCapabilityFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)

