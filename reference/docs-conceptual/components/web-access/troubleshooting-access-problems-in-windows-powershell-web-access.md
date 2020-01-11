---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: toegangs problemen in Windows Power shell-Internet toegang oplossen
ms.openlocfilehash: 818beffaf7df55ae36a154b7b751f9201c5b4299
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870180"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="c51c9-103">Toegangsproblemen in Windows PowerShell Web Access oplossen</span><span class="sxs-lookup"><span data-stu-id="c51c9-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="c51c9-104">Bijgewerkt: 24 juni 2013 (herziene versie van 23 augustus 2017)</span><span class="sxs-lookup"><span data-stu-id="c51c9-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="c51c9-105">Van toepassing op: Windows Server 2012 R2, WindowsServer 2012</span><span class="sxs-lookup"><span data-stu-id="c51c9-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="c51c9-106">In de volgende secties worden enkele veelvoorkomende problemen beschreven bij het maken van verbinding met een externe computer met Windows Power shell-webtoegang, en vindt u suggesties voor het oplossen van de problemen.</span><span class="sxs-lookup"><span data-stu-id="c51c9-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="c51c9-107">Aanmelding mislukt</span><span class="sxs-lookup"><span data-stu-id="c51c9-107">Sign-in failure</span></span>

<span data-ttu-id="c51c9-108">Deze fout kan de volgende oorzaken hebben.</span><span class="sxs-lookup"><span data-stu-id="c51c9-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="c51c9-109">Een autorisatieregel die de gebruiker toegang verleent tot de computer of een bepaalde sessieconfiguratie op de externe computer bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="c51c9-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="c51c9-110">Beveiliging van Windows Power shell-Internet toegang is beperkend; gebruikers moeten expliciet toegang tot externe computers worden verleend via autorisatie regels.</span><span class="sxs-lookup"><span data-stu-id="c51c9-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="c51c9-111">Zie [autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie over het maken van autorisatie regels.</span><span class="sxs-lookup"><span data-stu-id="c51c9-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="c51c9-112">De gebruiker heeft geen geautoriseerde toegang tot de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="c51c9-113">Dit wordt bepaald door toegangsbeheerlijsten (ACL's).</span><span class="sxs-lookup"><span data-stu-id="c51c9-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="c51c9-114">Zie [Aanmelden bij Windows Power shell-webtoegang](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)of het Windows Power shell-team blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c51c9-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="c51c9-115">Extern beheer van Windows Power shell wordt mogelijk niet ingeschakeld op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="c51c9-116">Controleer of extern beheer is ingeschakeld op de computer waarmee de gebruiker verbinding probeert te maken.</span><span class="sxs-lookup"><span data-stu-id="c51c9-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="c51c9-117">Zie [How to configure your computer voor externe toegang](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c51c9-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="c51c9-118">Interne server fout</span><span class="sxs-lookup"><span data-stu-id="c51c9-118">Internal Server Error</span></span>

<span data-ttu-id="c51c9-119">Wanneer gebruikers zich proberen aan te melden bij Windows Power shell-webtoegang in een Internet Explorer-venster, wordt een **interne server fout** pagina weer gegeven of reageert *Internet Explorer* niet meer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="c51c9-120">Dit probleem is specifiek voor Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="c51c9-121">Mogelijke oorzaak</span><span class="sxs-lookup"><span data-stu-id="c51c9-121">Possible cause</span></span>

<span data-ttu-id="c51c9-122">Dit probleem kan optreden bij gebruikers die zijn aangemeld met een domeinnaam die Chinese tekens bevat of als de naam van de gatewayserver een of meer Chinese tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="c51c9-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="c51c9-123">Tijdelijke oplossing</span><span class="sxs-lookup"><span data-stu-id="c51c9-123">Workaround</span></span>

1. <span data-ttu-id="c51c9-124">Internet Explorer 10 installeren en uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c51c9-124">Install and run Internet Explorer 10</span></span>
1. <span data-ttu-id="c51c9-125">Wijzig de instelling voor de **document modus** van Internet Explorer in *IE10* -standaarden.</span><span class="sxs-lookup"><span data-stu-id="c51c9-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="c51c9-126">Druk op **F12** om de Ontwikkelhulpprogramma's-console te openen</span><span class="sxs-lookup"><span data-stu-id="c51c9-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="c51c9-127">Klik in Internet Explorer 10 op **browser modus**en selecteer vervolgens *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="c51c9-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="c51c9-128">Klik op **document modus**en klik vervolgens op *IE10* -standaarden.</span><span class="sxs-lookup"><span data-stu-id="c51c9-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="c51c9-129">Druk nogmaals op **F12** om de Ontwikkelhulpprogramma's-console te sluiten.</span><span class="sxs-lookup"><span data-stu-id="c51c9-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="c51c9-130">Schakel automatische proxy configuratie uit in Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="c51c9-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="c51c9-131">Klik op **extra**en klik vervolgens op **Internet opties**.</span><span class="sxs-lookup"><span data-stu-id="c51c9-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="c51c9-132">Klik in het dialoog venster **Internet opties** op het tabblad **verbindingen** op **LAN-instellingen**.</span><span class="sxs-lookup"><span data-stu-id="c51c9-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="c51c9-133">Schakel het selectie vakje **instellingen automatisch detecteren** uit.</span><span class="sxs-lookup"><span data-stu-id="c51c9-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="c51c9-134">Klik op **OK**en klik nogmaals op **OK** om het dialoog venster *Internet opties* te sluiten.</span><span class="sxs-lookup"><span data-stu-id="c51c9-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="c51c9-135">Kan geen verbinding maken met een externe werkgroepcomputer</span><span class="sxs-lookup"><span data-stu-id="c51c9-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="c51c9-136">Als de doel computer lid is van een werk groep, gebruikt u de volgende syntaxis om uw gebruikers naam op te geven en u aan te melden bij de computer: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="c51c9-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="c51c9-137">Kan de beheerhulpprogramma's voor Webserver (IIS) niet vinden ook al is de functie geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="c51c9-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="c51c9-138">Als u Windows Power shell-webtoegang hebt geïnstalleerd met behulp van de cmdlet `Install-WindowsFeature`, worden beheer hulpprogramma's niet geïnstalleerd, tenzij de para meter **IncludeManagementTools** wordt toegevoegd aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c51c9-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the **IncludeManagementTools** parameter is added to the cmdlet.</span></span>

<span data-ttu-id="c51c9-139">Zie [Windows Power shell-webtoegang installeren met behulp van Windows Power shell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)voor een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="c51c9-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="c51c9-140">U kunt de IIS-beheer console en andere IIS-beheer hulpprogramma's die u nodig hebt, toevoegen door de hulpprogram ma's te selecteren in de **wizard functies en onderdelen toevoegen** die is gericht op de gateway server.</span><span class="sxs-lookup"><span data-stu-id="c51c9-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span> <span data-ttu-id="c51c9-141">De wizard functies en onderdelen toevoegen wordt geopend vanuit Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="c51c9-142">Windows Power shell Web Access-website is niet toegankelijk</span><span class="sxs-lookup"><span data-stu-id="c51c9-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="c51c9-143">Als verbeterde beveiliging is ingeschakeld in Internet Explorer (IE ESC), kunt u de website Windows Power shell Web Access toevoegen aan de lijst met vertrouwde sites.</span><span class="sxs-lookup"><span data-stu-id="c51c9-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="c51c9-144">Een minder aanbevolen aanpak door beveiligings Risico's is het uitschakelen van Internet Explorer ESC.</span><span class="sxs-lookup"><span data-stu-id="c51c9-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span> <span data-ttu-id="c51c9-145">U kunt IE ESC uitschakelen op de tegel eigenschappen op de pagina lokale server in Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="c51c9-146">Er is een autorisatie fout opgetreden.</span><span class="sxs-lookup"><span data-stu-id="c51c9-146">An authorization failure occurred.</span></span> <span data-ttu-id="c51c9-147">Controleer of u gemachtigd bent om verbinding te maken met de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="c51c9-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="c51c9-148">Het bovenstaande fout bericht wordt weer gegeven wanneer u verbinding probeert te maken wanneer de gateway server de doel computer is en zich ook in een werk groep bevindt.</span><span class="sxs-lookup"><span data-stu-id="c51c9-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="c51c9-149">Wanneer de gateway server ook de doel server is en deze zich in een werk groep bevindt, geeft u de gebruikers naam, de computer naam en de naam van de gebruikers groep op.</span><span class="sxs-lookup"><span data-stu-id="c51c9-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span> <span data-ttu-id="c51c9-150">Gebruik niet een punt (.) om de computer naam weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c51c9-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="c51c9-151">Scenario's en de juiste waarden</span><span class="sxs-lookup"><span data-stu-id="c51c9-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="c51c9-152">Alle cases</span><span class="sxs-lookup"><span data-stu-id="c51c9-152">All cases</span></span>

  <span data-ttu-id="c51c9-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="c51c9-153">Parameter</span></span>   |                                        <span data-ttu-id="c51c9-154">Value</span><span class="sxs-lookup"><span data-stu-id="c51c9-154">Value</span></span>
------------- | -----------------------------------------------------------------------------------
<span data-ttu-id="c51c9-155">UserName</span><span class="sxs-lookup"><span data-stu-id="c51c9-155">UserName</span></span>      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
<span data-ttu-id="c51c9-156">UserGroup</span><span class="sxs-lookup"><span data-stu-id="c51c9-156">UserGroup</span></span>     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
<span data-ttu-id="c51c9-157">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="c51c9-157">ComputerGroup</span></span> | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="c51c9-158">Gatewayserver bevindt zich in een domein.</span><span class="sxs-lookup"><span data-stu-id="c51c9-158">Gateway server is in a domain</span></span>

 <span data-ttu-id="c51c9-159">Parameter</span><span class="sxs-lookup"><span data-stu-id="c51c9-159">Parameter</span></span>   |                        <span data-ttu-id="c51c9-160">Value</span><span class="sxs-lookup"><span data-stu-id="c51c9-160">Value</span></span>
------------ | ----------------------------------------------------
<span data-ttu-id="c51c9-161">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c51c9-161">ComputerName</span></span> | <span data-ttu-id="c51c9-162">Volledig gekwalificeerde naam van gatewayserver of Localhost</span><span class="sxs-lookup"><span data-stu-id="c51c9-162">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="c51c9-163">Bestandsserver maakt deel uit van een werkgroep</span><span class="sxs-lookup"><span data-stu-id="c51c9-163">Gateway server is in a workgroup</span></span>

 <span data-ttu-id="c51c9-164">Parameter</span><span class="sxs-lookup"><span data-stu-id="c51c9-164">Parameter</span></span>   |    <span data-ttu-id="c51c9-165">Value</span><span class="sxs-lookup"><span data-stu-id="c51c9-165">Value</span></span>
------------ | -----------
<span data-ttu-id="c51c9-166">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c51c9-166">ComputerName</span></span> | <span data-ttu-id="c51c9-167">Servernaam</span><span class="sxs-lookup"><span data-stu-id="c51c9-167">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="c51c9-168">Gateway referenties</span><span class="sxs-lookup"><span data-stu-id="c51c9-168">Gateway credentials</span></span>

<span data-ttu-id="c51c9-169">Meld u aan bij een gatewayserver als doelcomputer met referenties die de volgende indeling hebben.</span><span class="sxs-lookup"><span data-stu-id="c51c9-169">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="c51c9-170">Er wordt een beveiligings-id (SID) weer gegeven in een autorisatie regel</span><span class="sxs-lookup"><span data-stu-id="c51c9-170">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="c51c9-171">Er wordt een beveiligings-id (SID) weer gegeven in een autorisatie regel in plaats van de syntaxis `user_name/computer_name`.</span><span class="sxs-lookup"><span data-stu-id="c51c9-171">A security identifier (SID) is displayed in an authorization rule instead of the syntax `user_name/computer_name`.</span></span>

<span data-ttu-id="c51c9-172">De regel is niet meer geldig of de Active Directory Domain Services-query is mislukt.</span><span class="sxs-lookup"><span data-stu-id="c51c9-172">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="c51c9-173">Een autorisatie regel is doorgaans niet geldig in scenario's waarin de gateway server zich in één keer in een werk groep bevond, maar later is toegevoegd aan een domein</span><span class="sxs-lookup"><span data-stu-id="c51c9-173">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="c51c9-174">Kan niet aanmelden met een regel als een IPv6-adres met een domein</span><span class="sxs-lookup"><span data-stu-id="c51c9-174">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="c51c9-175">Kan niet aanmelden bij een doelcomputer die is opgegeven in autorisatieregels als een IPv6-adres met een domein.</span><span class="sxs-lookup"><span data-stu-id="c51c9-175">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="c51c9-176">Autorisatieregels ondersteunen geen IPv6-adressen in de vorm van een domeinnaam.</span><span class="sxs-lookup"><span data-stu-id="c51c9-176">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="c51c9-177">Als u een doelcomputer wilt opgeven met behulp van een IPv6-adres, gebruikt u het oorspronkelijke IPv6-adres (dat dubbele punten bevat) in de autorisatieregel.</span><span class="sxs-lookup"><span data-stu-id="c51c9-177">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="c51c9-178">Zowel domein-als numerieke IPv6-adressen (met dubbele punten) worden ondersteund als de naam van de doel computer op de aanmeldings pagina van de Windows Power shell-webtoegang, maar niet in autorisatie regels.</span><span class="sxs-lookup"><span data-stu-id="c51c9-178">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="c51c9-179">Zie [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10))(Engelstalig) voor meer informatie over IPv6-adressen.</span><span class="sxs-lookup"><span data-stu-id="c51c9-179">For more information about IPv6 addresses, see [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span></span>

## <a name="see-also"></a><span data-ttu-id="c51c9-180">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c51c9-180">See Also</span></span>

- <span data-ttu-id="c51c9-181">[Autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="c51c9-181">[Authorization Rules and Security Features of Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span></span>
- <span data-ttu-id="c51c9-182">[De Windows Power shell-console van het web gebruiken](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="c51c9-182">[Use the Web-based Windows PowerShell Console](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span></span>
- [<span data-ttu-id="c51c9-183">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="c51c9-183">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
