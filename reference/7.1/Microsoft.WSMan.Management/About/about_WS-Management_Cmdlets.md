---
description: Biedt een overzicht van Web Services for Management (WS-Management) als achtergrond voor het gebruik van de WS-Management-cmdlets in Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: c9d89d0559bf844927976c78bde6fca58ffa8855
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390504"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="baca9-104">Over WS-Management-cmdlets</span><span class="sxs-lookup"><span data-stu-id="baca9-104">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="baca9-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="baca9-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="baca9-106">Biedt een overzicht van Web Services for Management (WS-Management) als achtergrond voor het gebruik van de WS-Management-cmdlets in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="baca9-106">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="baca9-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="baca9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="baca9-108">In dit onderwerp vindt u een overzicht van Web Services for Management (WS-Management) als achtergrond voor het gebruik van de WS-Management-cmdlets in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="baca9-108">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="baca9-109">Dit onderwerp bevat ook koppelingen naar meer informatie over WS-Management.</span><span class="sxs-lookup"><span data-stu-id="baca9-109">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="baca9-110">De micro soft-implementatie van WS-Management wordt ook wel Windows Remote Management (WinRM) genoemd.</span><span class="sxs-lookup"><span data-stu-id="baca9-110">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="baca9-111">Over WS-Management</span><span class="sxs-lookup"><span data-stu-id="baca9-111">About WS-Management</span></span>

<span data-ttu-id="baca9-112">Windows Remote Management is de micro soft-implementatie van het WS-Management-protocol, een standaard op basis van een gebruikers vriendelijke, firewall vriendelijk protocol waarmee hardware en besturings systemen van verschillende leveranciers kunnen samen werken.</span><span class="sxs-lookup"><span data-stu-id="baca9-112">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="baca9-113">De specificatie van het WS-Management-protocol biedt systemen een gemeen schappelijke manier om toegang te krijgen tot en Exchange-beheer gegevens in een IT-infra structuur (Information Technology).</span><span class="sxs-lookup"><span data-stu-id="baca9-113">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="baca9-114">WS-Management en IPMI (Intelligent Platform Management Interface), samen met de gebeurtenis verzamelaar, zijn onderdelen van de Windows-functies voor het beheer van hardware.</span><span class="sxs-lookup"><span data-stu-id="baca9-114">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="baca9-115">Het WS-Management-protocol is gebaseerd op de volgende standaard web service-specificaties: HTTPS, SOAP via HTTP (WS-I profile), SOAP 1,2, WS-Addressing, WS-overdracht, WS-Enumeration en WS-eventing.</span><span class="sxs-lookup"><span data-stu-id="baca9-115">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="baca9-116">WS-Management en WMI</span><span class="sxs-lookup"><span data-stu-id="baca9-116">WS-Management and WMI</span></span>

<span data-ttu-id="baca9-117">WS-Management kunnen worden gebruikt om gegevens op te halen die worden weer gegeven door Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="baca9-117">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="baca9-118">U kunt WMI-gegevens verkrijgen met scripts of toepassingen die gebruikmaken van de WS-Management Scripting-API of via het opdracht regel programma WinRM.</span><span class="sxs-lookup"><span data-stu-id="baca9-118">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="baca9-119">WS-Management ondersteunt de meeste vertrouwde WMI-klassen en-bewerkingen, inclusief Inge sloten objecten.</span><span class="sxs-lookup"><span data-stu-id="baca9-119">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="baca9-120">WS-Management kan gebruikmaken van WMI voor het verzamelen van gegevens over bronnen of voor het beheren van resources op een Windows-computer.</span><span class="sxs-lookup"><span data-stu-id="baca9-120">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="baca9-121">Dit betekent dat u gegevens kunt verkrijgen over objecten zoals schijven, netwerk adapters, services of processen in uw onderneming via de bestaande set WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="baca9-121">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="baca9-122">U hebt ook toegang tot de hardware-gegevens die beschikbaar zijn via de standaard WMI IPMI-provider.</span><span class="sxs-lookup"><span data-stu-id="baca9-122">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="baca9-123">Windows Power shell-provider (WSMan) WS-Management</span><span class="sxs-lookup"><span data-stu-id="baca9-123">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="baca9-124">De WSMan-provider biedt een hiërarchische weer gave van de beschik bare WS-Management configuratie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="baca9-124">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="baca9-125">De provider stelt u in staat om de verschillende WS-Management configuratie opties te verkennen en in te stellen.</span><span class="sxs-lookup"><span data-stu-id="baca9-125">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="baca9-126">WS-Management configuratie</span><span class="sxs-lookup"><span data-stu-id="baca9-126">WS-Management Configuration</span></span>

<span data-ttu-id="baca9-127">Als WS-Management niet is geïnstalleerd en geconfigureerd, externe toegang tot Windows Power shell is niet beschikbaar, de WS-Management-cmdlets worden niet uitgevoerd, WS-Management scripts niet worden uitgevoerd en de WSMan-provider kan geen gegevens bewerkingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="baca9-127">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="baca9-128">Het WS-Management opdracht regel programma, WinRM en gebeurtenis door sturen is ook afhankelijk van de WS-Management configuratie.</span><span class="sxs-lookup"><span data-stu-id="baca9-128">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="baca9-129">WS-Management-cmdlets</span><span class="sxs-lookup"><span data-stu-id="baca9-129">WS-Management Cmdlets</span></span>

<span data-ttu-id="baca9-130">WS-Management functionaliteit wordt in Windows Power shell geïmplementeerd via een module die een set cmdlets en de WSMan-provider bevat.</span><span class="sxs-lookup"><span data-stu-id="baca9-130">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="baca9-131">U kunt deze cmdlets gebruiken voor het volt ooien van de end-to-end taken die nodig zijn voor het beheren van WS-Management instellingen op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="baca9-131">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="baca9-132">De volgende WS-Management-cmdlets zijn beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="baca9-132">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="baca9-133">Verbindings-cmdlets</span><span class="sxs-lookup"><span data-stu-id="baca9-133">Connection Cmdlets</span></span>

- <span data-ttu-id="baca9-134">Connect-WSMan: verbindt de lokale computer met de WS-Management (WinRM)-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="baca9-134">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="baca9-135">Verbinding verbreken-WSMan: de verbinding van de lokale computer met de WS-Management-service (WinRM) op een externe computer wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="baca9-135">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="baca9-136">Management-Data-cmdlets</span><span class="sxs-lookup"><span data-stu-id="baca9-136">Management-Data Cmdlets</span></span>

- <span data-ttu-id="baca9-137">Get-WSManInstance: geeft beheer gegevens weer voor een resource-exemplaar dat is opgegeven door een resource-URI.</span><span class="sxs-lookup"><span data-stu-id="baca9-137">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="baca9-138">Invoke-WSManAction: roept een actie aan voor het doel object dat is opgegeven door de resource-URI en de selecters.</span><span class="sxs-lookup"><span data-stu-id="baca9-138">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="baca9-139">New-WSManInstance: maakt een nieuw beheer resource-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="baca9-139">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="baca9-140">Remove-WSManInstance: verwijdert een beheer resource-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="baca9-140">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="baca9-141">Set-WSManInstance: Hiermee wijzigt u de beheer gegevens die zijn gerelateerd aan een resource.</span><span class="sxs-lookup"><span data-stu-id="baca9-141">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="baca9-142">Cmdlets voor Setup en configuratie</span><span class="sxs-lookup"><span data-stu-id="baca9-142">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="baca9-143">Set-WSManQuickConfig: Hiermee configureert u de lokale computer voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="baca9-143">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="baca9-144">U kunt de cmdlet Set-WSManQuickConfig gebruiken om WS-Management te configureren om externe verbindingen met de WS-Management-service (WinRM) toe te staan.</span><span class="sxs-lookup"><span data-stu-id="baca9-144">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="baca9-145">Met de cmdlet Set-WSManQuickConfig worden de volgende bewerkingen uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="baca9-145">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="baca9-146">Hiermee wordt bepaald of de WS-Management-service (WinRM) wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="baca9-146">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="baca9-147">Als de WinRM-service niet wordt uitgevoerd, start de Set-WSManQuickConfig-cmdlet de service.</span><span class="sxs-lookup"><span data-stu-id="baca9-147">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="baca9-148">Hiermee stelt u het opstart type van de WS-Management (WinRM)-service in op automatisch.</span><span class="sxs-lookup"><span data-stu-id="baca9-148">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="baca9-149">Er wordt een listener gemaakt die aanvragen van elk IP-adres accepteert.</span><span class="sxs-lookup"><span data-stu-id="baca9-149">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="baca9-150">Het standaard transport protocol is HTTP.</span><span class="sxs-lookup"><span data-stu-id="baca9-150">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="baca9-151">Hiermee schakelt u een firewall-uitzonde ring voor WS-Management verkeer.</span><span class="sxs-lookup"><span data-stu-id="baca9-151">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="baca9-152">Opmerking: als u deze cmdlet wilt uitvoeren in Windows Vista, Windows Server 2008 en latere versies van Windows, moet u Windows Power shell starten met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="baca9-152">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="baca9-153">Test-WSMan: controleert of WS-Management is geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="baca9-153">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="baca9-154">De Test-WSMan-cmdlet test of de WS-Management-service (WinRM) wordt uitgevoerd en is geconfigureerd op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="baca9-154">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="baca9-155">Disable-WSManCredSSP: Hiermee schakelt u CredSSP-verificatie op een client computer uit.</span><span class="sxs-lookup"><span data-stu-id="baca9-155">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="baca9-156">Enable-WSManCredSSP: Hiermee schakelt u CredSSP-verificatie in op een client computer.</span><span class="sxs-lookup"><span data-stu-id="baca9-156">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="baca9-157">Get-WSManCredSSP: haalt de CredSSP-gerelateerde configuratie voor een client computer op.</span><span class="sxs-lookup"><span data-stu-id="baca9-157">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="baca9-158">WS-Management-specifieke cmdlets</span><span class="sxs-lookup"><span data-stu-id="baca9-158">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="baca9-159">New-WSManSessionOption: maakt een WSManSessionOption-object dat als invoer wordt gebruikt voor een of meer para meters van een WS-Management-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="baca9-159">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="baca9-160">Aanvullende informatie over WS-Management</span><span class="sxs-lookup"><span data-stu-id="baca9-160">Additional WS-Management Information</span></span>

<span data-ttu-id="baca9-161">Zie de volgende onderwerpen in de Windows-documentatie voor meer informatie over WS-Management.</span><span class="sxs-lookup"><span data-stu-id="baca9-161">For more information about WS-Management, see the following topics in the Windows documentation.</span></span>

[<span data-ttu-id="baca9-162">Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="baca9-162">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="baca9-163">Over Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="baca9-163">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="baca9-164">Installatie en configuratie voor Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="baca9-164">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="baca9-165">Architectuur van Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="baca9-165">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="baca9-166">WS-Management-protocol</span><span class="sxs-lookup"><span data-stu-id="baca9-166">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="baca9-167">Windows Remote Management en WMI</span><span class="sxs-lookup"><span data-stu-id="baca9-167">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="baca9-168">Bron-Uri's</span><span class="sxs-lookup"><span data-stu-id="baca9-168">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="baca9-169">Extern hardwarematig beheer</span><span class="sxs-lookup"><span data-stu-id="baca9-169">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="baca9-170">Gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="baca9-170">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="baca9-171">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="baca9-171">SEE ALSO</span></span>

[<span data-ttu-id="baca9-172">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="baca9-172">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="baca9-173">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="baca9-173">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="baca9-174">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="baca9-174">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="baca9-175">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="baca9-175">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="baca9-176">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="baca9-176">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="baca9-177">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="baca9-177">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="baca9-178">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="baca9-178">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="baca9-179">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="baca9-179">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="baca9-180">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="baca9-180">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="baca9-181">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="baca9-181">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="baca9-182">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="baca9-182">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="baca9-183">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="baca9-183">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
