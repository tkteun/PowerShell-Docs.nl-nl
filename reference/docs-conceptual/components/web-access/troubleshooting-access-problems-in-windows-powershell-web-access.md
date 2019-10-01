---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: toegangs problemen in Windows Power shell-Internet toegang oplossen
ms.openlocfilehash: 74cebbe418fecd21567ba9ecc7c561b51ac008fd
ms.sourcegitcommit: a35450f420dc10a02379f6e6f08a28ad11fe5a6d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71692241"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="a175b-103">Toegangsproblemen in Windows PowerShell Web Access oplossen</span><span class="sxs-lookup"><span data-stu-id="a175b-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="a175b-104">Vernieuwd 24 juni 2013 (herziene versie van 23 augustus 2017)</span><span class="sxs-lookup"><span data-stu-id="a175b-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="a175b-105">Van toepassing op: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a175b-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="a175b-106">In de volgende secties worden enkele veelvoorkomende problemen beschreven bij het maken van verbinding met een externe computer met Windows Power shell-webtoegang, en vindt u suggesties voor het oplossen van de problemen.</span><span class="sxs-lookup"><span data-stu-id="a175b-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="a175b-107">Aanmelding mislukt</span><span class="sxs-lookup"><span data-stu-id="a175b-107">Sign-in failure</span></span>

<span data-ttu-id="a175b-108">Deze fout kan de volgende oorzaken hebben.</span><span class="sxs-lookup"><span data-stu-id="a175b-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="a175b-109">Een autorisatieregel die de gebruiker toegang verleent tot de computer of een bepaalde sessieconfiguratie op de externe computer bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="a175b-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="a175b-110">Beveiliging van Windows Power shell-Internet toegang is beperkend; gebruikers moeten expliciet toegang tot externe computers worden verleend via autorisatie regels.</span><span class="sxs-lookup"><span data-stu-id="a175b-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="a175b-111">Zie [autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie over het maken van autorisatie regels.</span><span class="sxs-lookup"><span data-stu-id="a175b-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="a175b-112">De gebruiker heeft geen geautoriseerde toegang tot de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="a175b-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="a175b-113">Dit wordt bepaald door toegangsbeheerlijsten (ACL's).</span><span class="sxs-lookup"><span data-stu-id="a175b-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="a175b-114">Zie [Aanmelden bij Windows Power shell-webtoegang](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)of het Windows Power shell-team blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a175b-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="a175b-115">Extern beheer van Windows Power shell wordt mogelijk niet ingeschakeld op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="a175b-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="a175b-116">Controleer of extern beheer is ingeschakeld op de computer waarmee de gebruiker verbinding probeert te maken.</span><span class="sxs-lookup"><span data-stu-id="a175b-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="a175b-117">Zie [How to configure your computer voor externe toegang](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a175b-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="a175b-118">Interne server fout</span><span class="sxs-lookup"><span data-stu-id="a175b-118">Internal Server Error</span></span>

<span data-ttu-id="a175b-119">Wanneer gebruikers zich proberen aan te melden bij Windows Power shell-webtoegang in een Internet Explorer-venster, wordt een **interne server fout** pagina weer gegeven of reageert *Internet Explorer* niet meer.</span><span class="sxs-lookup"><span data-stu-id="a175b-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="a175b-120">Dit probleem is specifiek voor Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a175b-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="a175b-121">Mogelijke oorzaak</span><span class="sxs-lookup"><span data-stu-id="a175b-121">Possible cause</span></span>

<span data-ttu-id="a175b-122">Dit probleem kan optreden bij gebruikers die zijn aangemeld met een domeinnaam die Chinese tekens bevat of als de naam van de gatewayserver een of meer Chinese tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="a175b-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="a175b-123">Tijdelijke oplossing</span><span class="sxs-lookup"><span data-stu-id="a175b-123">Workaround</span></span>

1. <span data-ttu-id="a175b-124">Internet Explorer 10 installeren en uitvoeren</span><span class="sxs-lookup"><span data-stu-id="a175b-124">Install and run Internet Explorer 10</span></span>
1. <span data-ttu-id="a175b-125">Wijzig de instelling voor de **document modus** van Internet Explorer in *IE10* -standaarden.</span><span class="sxs-lookup"><span data-stu-id="a175b-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="a175b-126">Druk op **F12** om de Ontwikkelhulpprogramma's-console te openen</span><span class="sxs-lookup"><span data-stu-id="a175b-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="a175b-127">Klik in Internet Explorer 10 op **browser modus**en selecteer vervolgens *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="a175b-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="a175b-128">Klik op **document modus**en klik vervolgens op *IE10* -standaarden.</span><span class="sxs-lookup"><span data-stu-id="a175b-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="a175b-129">Druk nogmaals op **F12** om de Ontwikkelhulpprogramma's-console te sluiten.</span><span class="sxs-lookup"><span data-stu-id="a175b-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="a175b-130">Schakel automatische proxy configuratie uit in Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="a175b-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="a175b-131">Klik op **extra**en klik vervolgens op **Internet opties**.</span><span class="sxs-lookup"><span data-stu-id="a175b-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="a175b-132">Klik in het dialoog venster **Internet opties** op het tabblad **verbindingen** op **LAN-instellingen**.</span><span class="sxs-lookup"><span data-stu-id="a175b-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="a175b-133">Schakel het selectie vakje **instellingen automatisch detecteren** uit.</span><span class="sxs-lookup"><span data-stu-id="a175b-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="a175b-134">Klik op **OK**en klik nogmaals op **OK** om het dialoog venster *Internet opties* te sluiten.</span><span class="sxs-lookup"><span data-stu-id="a175b-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="a175b-135">Kan geen verbinding maken met een externe werkgroepcomputer</span><span class="sxs-lookup"><span data-stu-id="a175b-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="a175b-136">Als de doel computer lid is van een werk groep, gebruikt u de volgende syntaxis om uw gebruikers naam op te geven en zich aan te melden bij de computer: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="a175b-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="a175b-137">Kan de beheerhulpprogramma's voor Webserver (IIS) niet vinden ook al is de functie geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="a175b-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="a175b-138">Als u Windows Power shell-webtoegang hebt geïnstalleerd met behulp van de cmdlet `Install-WindowsFeature`, worden beheer hulpprogramma's niet geïnstalleerd, tenzij de para meter `-IncludeManagementTools` wordt toegevoegd aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a175b-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="a175b-139">Zie [Windows Power shell-webtoegang installeren met behulp van Windows Power shell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)voor een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="a175b-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="a175b-140">U kunt de IIS-beheer console en andere IIS-beheer hulpprogramma's die u nodig hebt, toevoegen door de hulpprogram ma's te selecteren in de **wizard functies en onderdelen toevoegen** die is gericht op de gateway server.</span><span class="sxs-lookup"><span data-stu-id="a175b-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="a175b-141">De wizard functies en onderdelen toevoegen wordt geopend vanuit Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="a175b-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="a175b-142">Windows Power shell Web Access-website is niet toegankelijk</span><span class="sxs-lookup"><span data-stu-id="a175b-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="a175b-143">Als verbeterde beveiliging is ingeschakeld in Internet Explorer (IE ESC), kunt u de website Windows Power shell Web Access toevoegen aan de lijst met vertrouwde sites.</span><span class="sxs-lookup"><span data-stu-id="a175b-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="a175b-144">Een minder aanbevolen aanpak door beveiligings Risico's is het uitschakelen van Internet Explorer ESC.</span><span class="sxs-lookup"><span data-stu-id="a175b-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="a175b-145">U kunt IE ESC uitschakelen op de tegel eigenschappen op de pagina lokale server in Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="a175b-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="a175b-146">Er is een autorisatie fout opgetreden.</span><span class="sxs-lookup"><span data-stu-id="a175b-146">An authorization failure occurred.</span></span> <span data-ttu-id="a175b-147">Controleer of u gemachtigd bent om verbinding te maken met de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="a175b-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="a175b-148">Het bovenstaande fout bericht wordt weer gegeven wanneer u verbinding probeert te maken wanneer de gateway server de doel computer is en zich ook in een werk groep bevindt.</span><span class="sxs-lookup"><span data-stu-id="a175b-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="a175b-149">Wanneer de gateway server ook de doel server is en deze zich in een werk groep bevindt, geeft u de gebruikers naam, de computer naam en de naam van de gebruikers groep op.</span><span class="sxs-lookup"><span data-stu-id="a175b-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="a175b-150">Gebruik niet een punt (.) om de computer naam weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a175b-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="a175b-151">Scenario's en de juiste waarden</span><span class="sxs-lookup"><span data-stu-id="a175b-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="a175b-152">Alle cases</span><span class="sxs-lookup"><span data-stu-id="a175b-152">All cases</span></span>

<span data-ttu-id="a175b-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="a175b-153">Parameter</span></span> | <span data-ttu-id="a175b-154">Value</span><span class="sxs-lookup"><span data-stu-id="a175b-154">Value</span></span>
-- | --
<span data-ttu-id="a175b-155">UserName</span><span class="sxs-lookup"><span data-stu-id="a175b-155">UserName</span></span> | <span data-ttu-id="a175b-156">Server @ no__t-0name @ no__t-1user @ no__t-2name</span><span class="sxs-lookup"><span data-stu-id="a175b-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="a175b-157">Localhost @ no__t-0user @ no__t-1name</span><span class="sxs-lookup"><span data-stu-id="a175b-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="a175b-158">. \\user @ no__t-1name</span><span class="sxs-lookup"><span data-stu-id="a175b-158">.\\user\_name</span></span>
<span data-ttu-id="a175b-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="a175b-159">UserGroup</span></span> | <span data-ttu-id="a175b-160">Server @ no__t-0name @ no__t-1user @ no__t-2group</span><span class="sxs-lookup"><span data-stu-id="a175b-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="a175b-161">Localhost @ no__t-0user @ no__t-1group</span><span class="sxs-lookup"><span data-stu-id="a175b-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="a175b-162">. \\user @ no__t-1group</span><span class="sxs-lookup"><span data-stu-id="a175b-162">.\\user\_group</span></span>
<span data-ttu-id="a175b-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="a175b-163">ComputerGroup</span></span> | <span data-ttu-id="a175b-164">Server @ no__t-0name @ no__t-1computer @ no__t-2group</span><span class="sxs-lookup"><span data-stu-id="a175b-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="a175b-165">Localhost @ no__t-0computer @ no__t-1group</span><span class="sxs-lookup"><span data-stu-id="a175b-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="a175b-166">. \\computer @ no__t-1group</span><span class="sxs-lookup"><span data-stu-id="a175b-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="a175b-167">Gatewayserver bevindt zich in een domein.</span><span class="sxs-lookup"><span data-stu-id="a175b-167">Gateway server is in a domain</span></span>

<span data-ttu-id="a175b-168">Parameter</span><span class="sxs-lookup"><span data-stu-id="a175b-168">Parameter</span></span> | <span data-ttu-id="a175b-169">Value</span><span class="sxs-lookup"><span data-stu-id="a175b-169">Value</span></span>
-- | --
<span data-ttu-id="a175b-170">Computernaam</span><span class="sxs-lookup"><span data-stu-id="a175b-170">ComputerName</span></span> | <span data-ttu-id="a175b-171">Volledig gekwalificeerde naam van gatewayserver of Localhost</span><span class="sxs-lookup"><span data-stu-id="a175b-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="a175b-172">Bestandsserver maakt deel uit van een werkgroep</span><span class="sxs-lookup"><span data-stu-id="a175b-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="a175b-173">Parameter</span><span class="sxs-lookup"><span data-stu-id="a175b-173">Parameter</span></span> | <span data-ttu-id="a175b-174">Value</span><span class="sxs-lookup"><span data-stu-id="a175b-174">Value</span></span>
-- | --
<span data-ttu-id="a175b-175">Computernaam</span><span class="sxs-lookup"><span data-stu-id="a175b-175">ComputerName</span></span> | <span data-ttu-id="a175b-176">Servernaam</span><span class="sxs-lookup"><span data-stu-id="a175b-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="a175b-177">Gateway referenties</span><span class="sxs-lookup"><span data-stu-id="a175b-177">Gateway credentials</span></span>

<span data-ttu-id="a175b-178">Meld u aan bij een gatewayserver als doelcomputer met referenties die de volgende indeling hebben.</span><span class="sxs-lookup"><span data-stu-id="a175b-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="a175b-179">Server @ no__t-0name @ no__t-1user @ no__t-2name</span><span class="sxs-lookup"><span data-stu-id="a175b-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="a175b-180">Localhost @ no__t-0user @ no__t-1name</span><span class="sxs-lookup"><span data-stu-id="a175b-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="a175b-181">. \\user @ no__t-1name</span><span class="sxs-lookup"><span data-stu-id="a175b-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="a175b-182">Er wordt een beveiligings-id (SID) weer gegeven in een autorisatie regel</span><span class="sxs-lookup"><span data-stu-id="a175b-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="a175b-183">Er wordt een beveiligings-id (SID) weer gegeven in een autorisatie regel in plaats van de syntaxis gebruiker @ no__t-0name/computer @ no__t-1name.</span><span class="sxs-lookup"><span data-stu-id="a175b-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="a175b-184">De regel is niet meer geldig of de Active Directory Domain Services-query is mislukt.</span><span class="sxs-lookup"><span data-stu-id="a175b-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="a175b-185">Een autorisatie regel is doorgaans niet geldig in scenario's waarin de gateway server zich in één keer in een werk groep bevond, maar later is toegevoegd aan een domein</span><span class="sxs-lookup"><span data-stu-id="a175b-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="a175b-186">Kan niet aanmelden met een regel als een IPv6-adres met een domein</span><span class="sxs-lookup"><span data-stu-id="a175b-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="a175b-187">Kan niet aanmelden bij een doelcomputer die is opgegeven in autorisatieregels als een IPv6-adres met een domein.</span><span class="sxs-lookup"><span data-stu-id="a175b-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="a175b-188">Autorisatieregels ondersteunen geen IPv6-adressen in de vorm van een domeinnaam.</span><span class="sxs-lookup"><span data-stu-id="a175b-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="a175b-189">Als u een doelcomputer wilt opgeven met behulp van een IPv6-adres, gebruikt u het oorspronkelijke IPv6-adres (dat dubbele punten bevat) in de autorisatieregel.</span><span class="sxs-lookup"><span data-stu-id="a175b-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="a175b-190">Zowel domein-als numerieke IPv6-adressen (met dubbele punten) worden ondersteund als de naam van de doel computer op de aanmeldings pagina van de Windows Power shell-webtoegang, maar niet in autorisatie regels.</span><span class="sxs-lookup"><span data-stu-id="a175b-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="a175b-191">Zie [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)(Engelstalig) voor meer informatie over IPv6-adressen.</span><span class="sxs-lookup"><span data-stu-id="a175b-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="a175b-192">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a175b-192">See Also</span></span>

- <span data-ttu-id="a175b-193">[Autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="a175b-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="a175b-194">[De Windows Power shell-console van het web gebruiken](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="a175b-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="a175b-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="a175b-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
