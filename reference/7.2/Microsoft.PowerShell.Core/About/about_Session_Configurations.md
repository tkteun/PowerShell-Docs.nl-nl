---
description: Hierin worden de sessie configuraties beschreven, waarmee wordt bepaald welke gebruikers op afstand verbinding kunnen maken met de computer en welke opdrachten ze kunnen uitvoeren.
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 4c6d5494f49bc271a7fe128fbce7b27c9d1f675f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706080"
---
# <a name="about-session-configurations"></a><span data-ttu-id="bf572-103">Over sessie configuraties</span><span class="sxs-lookup"><span data-stu-id="bf572-103">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="bf572-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bf572-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bf572-105">Hierin worden de sessie configuraties beschreven, waarmee wordt bepaald welke gebruikers op afstand verbinding kunnen maken met de computer en welke opdrachten ze kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bf572-105">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf572-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bf572-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="bf572-107">Een sessie configuratie, ook wel een ' eind punt ' genoemd, is een groep instellingen op de lokale computer die de omgeving definiëren voor de Power shell-sessies die worden gemaakt wanneer externe of lokale gebruikers verbinding maken met Power shell op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-107">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="bf572-108">Beheerders van de computer kunnen sessie configuraties gebruiken om de computer te beveiligen en aangepaste omgevingen te definiëren voor gebruikers die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-108">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="bf572-109">Beheerders kunnen ook sessie configuraties gebruiken om de machtigingen te bepalen die nodig zijn om op afstand verbinding te maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-109">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="bf572-110">Standaard hebben alleen leden van de groep Administrators toestemming om de sessie configuratie te gebruiken om extern verbinding te maken, maar u kunt de standaard instellingen wijzigen zodat alle gebruikers of geselecteerde gebruikers extern verbinding kunnen maken met uw computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-110">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="bf572-111">Vanaf Power Shell 3,0 kunt u een configuratie bestand voor de sessie gebruiken om de elementen van een sessie configuratie te definiëren.</span><span class="sxs-lookup"><span data-stu-id="bf572-111">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="bf572-112">Met deze functie kunt u eenvoudig sessies aanpassen zonder code te schrijven en de eigenschappen van een sessie configuratie detecteren.</span><span class="sxs-lookup"><span data-stu-id="bf572-112">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="bf572-113">Gebruik de cmdlet New-PSSessionConfiguration om een sessie configuratie bestand te maken.</span><span class="sxs-lookup"><span data-stu-id="bf572-113">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="bf572-114">Zie [about_Session_Configuration_Files](about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="bf572-114">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="bf572-115">Sessie configuraties zijn een functie van webservices voor beheer op basis van Power shell voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="bf572-115">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="bf572-116">Ze worden alleen gebruikt wanneer u de cmdlets New-PSSession, Invoke-Command of Enter-PSSession gebruikt om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-116">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="bf572-117">Opmerking: als u de sessie configuraties wilt beheren, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bf572-117">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="bf572-118">Over sessie configuraties</span><span class="sxs-lookup"><span data-stu-id="bf572-118">About Session Configurations</span></span>

<span data-ttu-id="bf572-119">Elke Power shell-sessie gebruikt een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bf572-119">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="bf572-120">Dit omvat permanente sessies die u maakt met behulp van de New-PSSession-of Enter-PSSession-cmdlets en de tijdelijke sessies die Power Shell maakt wanneer u de para meter ComputerName gebruikt van een cmdlet die gebruikmaakt van op WS-Management gebaseerde externe technologieën, zoals invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="bf572-120">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="bf572-121">Beheerders kunnen sessie configuraties gebruiken om de bronnen van de computer te beveiligen en om aangepaste omgevingen te maken voor gebruikers die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-121">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="bf572-122">U kunt bijvoorbeeld een sessie configuratie gebruiken om de grootte van objecten die de computer ontvangt in de sessie te beperken, om de taal modus van de sessie te definiëren en om de cmdlets, providers en functies op te geven die beschikbaar zijn in de sessie.</span><span class="sxs-lookup"><span data-stu-id="bf572-122">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="bf572-123">Door de security descriptor van een sessie configuratie te configureren, bepaalt u wie de sessie configuratie kan gebruiken om verbinding te maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-123">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="bf572-124">Gebruikers moeten beschikken over de machtiging uitvoeren voor een sessie configuratie om deze te gebruiken in een sessie.</span><span class="sxs-lookup"><span data-stu-id="bf572-124">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="bf572-125">Als een gebruiker niet over de vereiste machtigingen beschikt om een van de sessie configuraties op een computer te gebruiken, kan de gebruiker niet op afstand verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-125">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="bf572-126">Standaard hebben alleen beheerders van de computer toestemming om de standaard sessie configuraties te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf572-126">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="bf572-127">Maar u kunt de security descriptors wijzigen zodat iedereen, niemand, of alleen geselecteerde gebruikers de sessie configuraties op uw computer kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf572-127">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="bf572-128">Ingebouwde sessie configuraties</span><span class="sxs-lookup"><span data-stu-id="bf572-128">Built-in Session Configurations</span></span>

<span data-ttu-id="bf572-129">Power Shell 3,0 bevat ingebouwde sessie configuraties met de naam micro soft. Power shell en micro soft. Power shell. workflow.</span><span class="sxs-lookup"><span data-stu-id="bf572-129">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="bf572-130">Op computers met 64-bits versies van Windows biedt Power shell ook micro soft. PowerShell32, een 32-bits sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bf572-130">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="bf572-131">De configuratie van de micro soft. Power shell-sessie wordt standaard gebruikt voor sessies, dat wil zeggen, wanneer een opdracht voor het maken van een sessie niet de para meter configuratiepad van de cmdlet New-PSSession, Enter-PSSession of Invoke-Command bevat.</span><span class="sxs-lookup"><span data-stu-id="bf572-131">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="bf572-132">Met de security descriptors voor de standaard sessie configuraties kunnen alleen leden van de groep Administrators op de lokale computer deze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf572-132">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="bf572-133">Als zodanig kunnen alleen leden van de groep Administrators op afstand verbinding maken met de computer, tenzij u de standaard instellingen wijzigt.</span><span class="sxs-lookup"><span data-stu-id="bf572-133">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="bf572-134">U kunt de standaard sessie configuraties wijzigen met behulp van de voorkeurs variabele $PSSessionConfigurationName.</span><span class="sxs-lookup"><span data-stu-id="bf572-134">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="bf572-135">Zie about_Preference_Variables voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf572-135">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="bf572-136">Sessie configuraties weer geven op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="bf572-136">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="bf572-137">Gebruik de cmdlet Get-PSSessionConfiguration om de sessie configuraties op uw lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="bf572-137">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="bf572-138">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bf572-138">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="bf572-139">Het sessie configuratie object wordt uitgevouwen in Power Shell 3,0 om de eigenschappen van de sessie configuratie weer te geven die zijn geconfigureerd met behulp van een configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="bf572-139">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="bf572-140">Als u bijvoorbeeld alle eigenschappen van een sessie configuratie object wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="bf572-140">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="bf572-141">U kunt ook de WSMan-provider in Power shell gebruiken om de sessie configuraties weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bf572-141">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="bf572-142">De WSMan-provider maakt een WSMAN:-station in uw sessie.</span><span class="sxs-lookup"><span data-stu-id="bf572-142">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="bf572-143">In het WSMAN: station bevinden de sessie configuraties zich in het knoop punt van de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="bf572-143">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="bf572-144">(Alle sessie configuraties bevinden zich in het knoop punt van de invoeg toepassing, maar er zijn items in het knoop punt van de invoeg toepassing die geen sessie configuraties zijn.)</span><span class="sxs-lookup"><span data-stu-id="bf572-144">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="bf572-145">Als u bijvoorbeeld de sessie configuraties op de lokale computer wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="bf572-145">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="bf572-146">Sessie configuraties weer geven op een externe computer</span><span class="sxs-lookup"><span data-stu-id="bf572-146">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="bf572-147">Als u de sessie configuraties op een externe computer wilt weer geven, gebruikt u de Connect-WSMan-cmdlet om een notitie voor de externe computer toe te voegen aan het WSMAN:-station op uw lokale computer en vervolgens het WSMAN:-station te gebruiken om de sessie configuraties weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bf572-147">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="bf572-148">Met de volgende opdracht wordt bijvoorbeeld een knoop punt voor de externe computer Server01 toegevoegd aan het WSMAN:-station op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-148">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="bf572-149">Wanneer de opdracht is voltooid, kunt u naar het knoop punt voor de Server01-computer navigeren om de sessie configuraties weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bf572-149">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="bf572-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bf572-150">For example:</span></span>

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="bf572-151">De security descriptor van een sessie configuratie wijzigen</span><span class="sxs-lookup"><span data-stu-id="bf572-151">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="bf572-152">In Windows Server 2012 en nieuwere versies van Windows Server worden de ingebouwde sessie configuraties standaard ingeschakeld voor externe gebruikers.</span><span class="sxs-lookup"><span data-stu-id="bf572-152">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="bf572-153">In andere ondersteunde versies van Windows moet u de security descriptors van de sessie configuraties wijzigen om externe toegang toe te staan.</span><span class="sxs-lookup"><span data-stu-id="bf572-153">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="bf572-154">Gebruik de cmdlet Enable-PSRemoting om externe toegang tot de sessie configuraties op de computer in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="bf572-154">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="bf572-155">Met deze cmdlet worden twee sessie configuraties gemaakt:</span><span class="sxs-lookup"><span data-stu-id="bf572-155">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="bf572-156">met de naam die is gedefinieerd als: Power shell.</span><span class="sxs-lookup"><span data-stu-id="bf572-156">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="bf572-157">+ "huidige Power shell-versie"</span><span class="sxs-lookup"><span data-stu-id="bf572-157">+ "current PowerShell version"</span></span>
- <span data-ttu-id="bf572-158">met de naam Power shell. 6, die niet is gekoppeld aan een specifieke Power shell-versie.</span><span class="sxs-lookup"><span data-stu-id="bf572-158">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="bf572-159">Standaard hebben alleen leden van de groep Administrators op de computer de machtiging uitvoeren voor de standaard sessie configuraties, maar u kunt de security descriptors wijzigen op de standaard sessie configuraties en op de sessie configuraties die u maakt.</span><span class="sxs-lookup"><span data-stu-id="bf572-159">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="bf572-160">Als u andere gebruikers toestemming wilt geven om op afstand verbinding te maken met de computer, gebruikt u de cmdlet Set-PSSessionConfiguration om ' Execute ' machtigingen voor die gebruikers toe te voegen aan de security descriptors van de micro soft. Power shell-en micro soft. PowerShell32-sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="bf572-160">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="bf572-161">Met de volgende opdracht wordt bijvoorbeeld een eigenschappen pagina geopend waarmee u de security descriptor voor de standaard sessie configuratie van micro soft. Power shell kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf572-161">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="bf572-162">Als u iedereen toestemming wilt verlenen voor alle sessie configuraties op de computer, gebruikt u de cmdlet Disable-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bf572-162">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="bf572-163">Met de volgende opdracht worden bijvoorbeeld de standaard sessie configuraties op de computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bf572-163">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="bf572-164">Als u wilt voor komen dat externe gebruikers verbinding maken met de computer, maar lokale gebruikers verbinding laten maken, gebruikt u de cmdlet Disable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="bf572-164">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="bf572-165">Disable-PSRemoting voegt een vermelding ' Network_Deny_All ' toe aan alle sessie configuraties op de computer.</span><span class="sxs-lookup"><span data-stu-id="bf572-165">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="bf572-166">Als u wilt dat externe gebruikers alle sessie configuraties op de computer kunnen gebruiken, gebruikt u de cmdlet Enable-PSRemoting of Enable-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bf572-166">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="bf572-167">Met de volgende opdracht wordt bijvoorbeeld externe toegang tot de ingebouwde sessie configuraties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bf572-167">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="bf572-168">Gebruik de Set-PSSessionConfiguration-cmdlet om andere wijzigingen aan te brengen in de security descriptor van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bf572-168">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="bf572-169">Gebruik de para meter SecurityDescriptorSDDL om een SDDL-teken reeks waarde in te dienen.</span><span class="sxs-lookup"><span data-stu-id="bf572-169">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="bf572-170">Gebruik de para meter ShowSecurityDescriptorUI om een eigenschappen venster van de gebruikers interface weer te geven waarmee u een nieuwe SDDL kunt maken.</span><span class="sxs-lookup"><span data-stu-id="bf572-170">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="bf572-171">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bf572-171">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="bf572-172">Een nieuwe sessie configuratie maken</span><span class="sxs-lookup"><span data-stu-id="bf572-172">Creating a New Session Configuration</span></span>

<span data-ttu-id="bf572-173">Als u een nieuwe sessie configuratie wilt maken op de lokale computer, gebruikt u de cmdlet Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bf572-173">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="bf572-174">Als u de nieuwe sessie configuratie wilt definiëren, kunt u een C#-assembly, een Power shell-script en de para meters van de cmdlet Register-PSSessionConfiguration gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf572-174">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="bf572-175">Met de volgende opdracht maakt u bijvoorbeeld een sessie configuratie die identiek is aan de configuratie van de micro soft. Power shell-sessie, met uitzonde ring van de gegevens die zijn ontvangen van een externe opdracht tot 20 Mega bytes (MB).</span><span class="sxs-lookup"><span data-stu-id="bf572-175">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="bf572-176">(De standaard waarde is 50 MB).</span><span class="sxs-lookup"><span data-stu-id="bf572-176">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="bf572-177">Wanneer u een sessie configuratie maakt, kunt u deze beheren met behulp van de andere sessie configuratie-cmdlets en deze wordt weer gegeven in het station WSMAN:.</span><span class="sxs-lookup"><span data-stu-id="bf572-177">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="bf572-178">Zie REGI ster-PSSessionConfiguration voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf572-178">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="bf572-179">Een sessie configuratie verwijderen</span><span class="sxs-lookup"><span data-stu-id="bf572-179">Removing a Session Configuration</span></span>

<span data-ttu-id="bf572-180">Als u een sessie configuratie wilt verwijderen van de lokale computer, gebruikt u de cmdlet Unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bf572-180">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="bf572-181">Met de volgende opdracht wordt bijvoorbeeld de NewConfig-sessie configuratie van de computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="bf572-181">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="bf572-182">Zie unregister-PSSessionConfiguration voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf572-182">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="bf572-183">Een sessie configuratie herstellen</span><span class="sxs-lookup"><span data-stu-id="bf572-183">Restoring a Session Configuration</span></span>

<span data-ttu-id="bf572-184">Als u een standaard sessie configuratie wilt herstellen die per ongeluk is verwijderd (niet geregistreerd), gebruikt u de Enable-PSRemoting-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf572-184">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="bf572-185">Met de cmdlet Enable-PSRemoting worden alle standaard-sessie configuraties die niet bestaan op de computer opnieuw gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bf572-185">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="bf572-186">De eigenschaps waarden van bestaande sessie configuraties worden niet overschreven of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bf572-186">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="bf572-187">Als u de oorspronkelijke eigenschaps waarden van een standaard sessie configuratie wilt herstellen, gebruikt u de Unregister-PSSessionConfiguration om de sessie configuratie te verwijderen en gebruikt u vervolgens de Enable-PSRemoting cmdlet om deze opnieuw te maken.</span><span class="sxs-lookup"><span data-stu-id="bf572-187">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="bf572-188">Een sessie configuratie selecteren</span><span class="sxs-lookup"><span data-stu-id="bf572-188">Selecting a Session Configuration</span></span>

<span data-ttu-id="bf572-189">Als u een bepaalde sessie configuratie voor een sessie wilt selecteren, gebruikt u de para meter configuratiepad van New-PSSession, Enter-PSSession of invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="bf572-189">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="bf572-190">Met deze opdracht wordt bijvoorbeeld de cmdlet New-PSSession gebruikt om een PSSession op de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="bf572-190">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="bf572-191">De opdracht gebruikt de para meter configuratiepad om de WithProfile-configuratie op de Server01-computer te selecteren.</span><span class="sxs-lookup"><span data-stu-id="bf572-191">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="bf572-192">Deze opdracht kan alleen worden uitgevoerd als de huidige gebruiker gemachtigd is om de WithProfile-sessie configuratie te gebruiken of de referenties op te geven van een gebruiker die de vereiste machtigingen heeft.</span><span class="sxs-lookup"><span data-stu-id="bf572-192">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="bf572-193">U kunt ook de $PSSessionConfigurationName voorkeurs variabele gebruiken om de standaard sessie configuratie op de computer te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf572-193">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="bf572-194">Zie about_Preference_Variables voor meer informatie over de $PSSessionConfigurationName voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="bf572-194">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="bf572-195">WOORD</span><span class="sxs-lookup"><span data-stu-id="bf572-195">KEYWORDS</span></span>

<span data-ttu-id="bf572-196">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="bf572-196">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="bf572-197">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="bf572-197">SEE ALSO</span></span>

[<span data-ttu-id="bf572-198">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="bf572-198">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="bf572-199">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="bf572-199">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="bf572-200">about_Remote</span><span class="sxs-lookup"><span data-stu-id="bf572-200">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="bf572-201">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="bf572-201">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="bf572-202">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="bf572-202">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="bf572-203">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf572-203">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="bf572-204">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf572-204">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="bf572-205">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf572-205">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="bf572-206">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bf572-206">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="bf572-207">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf572-207">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="bf572-208">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf572-208">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="bf572-209">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bf572-209">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="bf572-210">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf572-210">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

