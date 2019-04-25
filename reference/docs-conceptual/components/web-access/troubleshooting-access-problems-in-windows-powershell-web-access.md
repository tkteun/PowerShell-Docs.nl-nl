---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: toegangsproblemen in windows powershell-webtoegang oplossen
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086592"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="39c2c-103">Toegangsproblemen in Windows PowerShell Web Access oplossen</span><span class="sxs-lookup"><span data-stu-id="39c2c-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="39c2c-104">Bijgewerkt: Juni 24 2013 (herziene versie van 23 augustus 2017)</span><span class="sxs-lookup"><span data-stu-id="39c2c-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="39c2c-105">Van toepassing op: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="39c2c-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="39c2c-106">De volgende secties enkele veelvoorkomende problemen identificeren tijdens het verbinding maken met een externe computer met Windows PowerShell-webtoegang en de tabel bevat suggesties voor het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="39c2c-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="39c2c-107">Aanmelding mislukt</span><span class="sxs-lookup"><span data-stu-id="39c2c-107">Sign-in failure</span></span>

<span data-ttu-id="39c2c-108">Deze fout kan de volgende oorzaken hebben.</span><span class="sxs-lookup"><span data-stu-id="39c2c-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="39c2c-109">Een autorisatieregel die de gebruiker toegang verleent tot de computer of een bepaalde sessieconfiguratie op de externe computer bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="39c2c-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="39c2c-110">Beveiliging van Windows PowerShell-webtoegang is beperkend; gebruikers moet expliciet toegang tot externe computers worden verleend via autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="39c2c-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="39c2c-111">Zie voor meer informatie over het maken van autorisatieregels [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="39c2c-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="39c2c-112">De gebruiker heeft geen geautoriseerde toegang tot de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="39c2c-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="39c2c-113">Dit wordt bepaald door toegangsbeheerlijsten (ACL's).</span><span class="sxs-lookup"><span data-stu-id="39c2c-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="39c2c-114">Zie voor meer informatie, [aanmelden bij Windows PowerShell-webtoegang](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), of de Windows PowerShell Team Blog.</span><span class="sxs-lookup"><span data-stu-id="39c2c-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="39c2c-115">Extern beheer van Windows PowerShell kan niet worden ingeschakeld op de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="39c2c-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="39c2c-116">Controleer of extern beheer is ingeschakeld op de computer waarop de gebruiker probeert om verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="39c2c-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="39c2c-117">Zie voor meer informatie, [hoe u uw Computer configureren voor externe toegang](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="39c2c-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="39c2c-118">Interne serverfout</span><span class="sxs-lookup"><span data-stu-id="39c2c-118">Internal Server Error</span></span>

<span data-ttu-id="39c2c-119">Wanneer gebruikers proberen zich aanmeldt bij Windows PowerShell-webtoegang in een venster van Internet Explorer, worden ze weergegeven een **interne serverfout** pagina of *Internet Explorer* reageert niet meer.</span><span class="sxs-lookup"><span data-stu-id="39c2c-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="39c2c-120">Dit probleem is specifiek voor Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="39c2c-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="39c2c-121">Mogelijke oorzaak</span><span class="sxs-lookup"><span data-stu-id="39c2c-121">Possible cause</span></span>

<span data-ttu-id="39c2c-122">Dit probleem kan optreden bij gebruikers die zijn aangemeld met een domeinnaam die Chinese tekens bevat of als de naam van de gatewayserver een of meer Chinese tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="39c2c-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="39c2c-123">Tijdelijke oplossing</span><span class="sxs-lookup"><span data-stu-id="39c2c-123">Workaround</span></span>

1. [<span data-ttu-id="39c2c-124">Installeren en uitvoeren van Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="39c2c-124">Install and run Internet Explorer 10</span></span>](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="39c2c-125">Wijzigen van Internet Explorer **documentmodus** instelt op *IE10* standaarden.</span><span class="sxs-lookup"><span data-stu-id="39c2c-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="39c2c-126">Druk op **F12** openen van de console ontwikkelhulpprogramma's</span><span class="sxs-lookup"><span data-stu-id="39c2c-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="39c2c-127">Klik in Internet Explorer 10 op **Browsermodus**, en selecteer vervolgens *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="39c2c-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="39c2c-128">Klik op **documentmodus**, en klik vervolgens op *IE10* standaarden.</span><span class="sxs-lookup"><span data-stu-id="39c2c-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="39c2c-129">Druk op **F12** opnieuw uit te sluiten van de console ontwikkelhulpprogramma's.</span><span class="sxs-lookup"><span data-stu-id="39c2c-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="39c2c-130">Schakel automatische proxyconfiguratie in Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="39c2c-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="39c2c-131">Klik op **extra**, en klik vervolgens op **Internetopties**.</span><span class="sxs-lookup"><span data-stu-id="39c2c-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="39c2c-132">In de **Internetopties** dialoogvenster op de **verbindingen** tabblad **LAN-instellingen**.</span><span class="sxs-lookup"><span data-stu-id="39c2c-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="39c2c-133">Schakel de **-instellingen automatisch detecteren** selectievakje.</span><span class="sxs-lookup"><span data-stu-id="39c2c-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="39c2c-134">Klik op **OK**, en klik vervolgens op **OK** opnieuw uit te sluiten de *Internetopties* in het dialoogvenster.</span><span class="sxs-lookup"><span data-stu-id="39c2c-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="39c2c-135">Kan geen verbinding maken met een externe werkgroepcomputer</span><span class="sxs-lookup"><span data-stu-id="39c2c-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="39c2c-136">Als de doelcomputer lid is van een werkgroep, gebruikt u de volgende syntaxis om te bieden uw gebruikersnaam en meld u aan bij de computer: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="39c2c-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="39c2c-137">Kan de beheerhulpprogramma's voor Webserver (IIS) niet vinden ook al is de functie geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="39c2c-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="39c2c-138">Als u Windows PowerShell-webtoegang geïnstalleerd met behulp van de `Install-WindowsFeature` cmdlet, management-hulpprogramma's zijn niet geïnstalleerd, tenzij de `-IncludeManagementTools` parameter is toegevoegd aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39c2c-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="39c2c-139">Zie voor een voorbeeld [Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="39c2c-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="39c2c-140">U kunt de IIS Manager-console toevoegen en andere IIS-beheerprogramma's die u nodig hebt, selecteert u de hulpprogramma's in een **functies Wizard Functies toevoegen en** sessie die is gericht op de gateway-server.</span><span class="sxs-lookup"><span data-stu-id="39c2c-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="39c2c-141">De toevoegen Wizard functies en onderdelen wordt geopend vanuit binnen Server Manager.</span><span class="sxs-lookup"><span data-stu-id="39c2c-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="39c2c-142">Windows PowerShell Web Access-website is niet toegankelijk</span><span class="sxs-lookup"><span data-stu-id="39c2c-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="39c2c-143">Als Verbeterde beveiliging is ingeschakeld in Internet Explorer (IE ESC), kunt u de Windows PowerShell Web Access-website toevoegen aan de lijst met vertrouwde sites.</span><span class="sxs-lookup"><span data-stu-id="39c2c-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="39c2c-144">Een minder aanbevolen benadering, vanwege een beveiligingsrisico's, is het IE ESC uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="39c2c-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="39c2c-145">U kunt IE ESC uitschakelen in de tegel eigenschappen op de lokale Server-pagina in Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="39c2c-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="39c2c-146">Er is een Autorisatiefout opgetreden.</span><span class="sxs-lookup"><span data-stu-id="39c2c-146">An authorization failure occurred.</span></span> <span data-ttu-id="39c2c-147">Controleer of u gemachtigd bent om verbinding te maken met de doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="39c2c-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="39c2c-148">De bovenstaande foutbericht wordt weergegeven tijdens het verbinding maken wanneer de gatewayserver de doelcomputer is en ook in een werkgroep is.</span><span class="sxs-lookup"><span data-stu-id="39c2c-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="39c2c-149">Wanneer de gatewayserver ook de doelserver is en deel uitmaakt van een werkgroep, geeft u de gebruikersnaam, computernaam en naam van de gebruikersgroep.</span><span class="sxs-lookup"><span data-stu-id="39c2c-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="39c2c-150">Gebruik een punt (.) niet op zichzelf voor de computernaam van de.</span><span class="sxs-lookup"><span data-stu-id="39c2c-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="39c2c-151">Scenario's en de juiste waarden</span><span class="sxs-lookup"><span data-stu-id="39c2c-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="39c2c-152">Alle aanvragen</span><span class="sxs-lookup"><span data-stu-id="39c2c-152">All cases</span></span>

<span data-ttu-id="39c2c-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="39c2c-153">Parameter</span></span> | <span data-ttu-id="39c2c-154">Waarde</span><span class="sxs-lookup"><span data-stu-id="39c2c-154">Value</span></span>
-- | --
<span data-ttu-id="39c2c-155">UserName</span><span class="sxs-lookup"><span data-stu-id="39c2c-155">UserName</span></span> | <span data-ttu-id="39c2c-156">Server\_naam\\gebruiker\_naam</span><span class="sxs-lookup"><span data-stu-id="39c2c-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="39c2c-157">Localhost\\gebruiker\_naam</span><span class="sxs-lookup"><span data-stu-id="39c2c-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="39c2c-158">. \\gebruiker\_naam</span><span class="sxs-lookup"><span data-stu-id="39c2c-158">.\\user\_name</span></span>
<span data-ttu-id="39c2c-159">Gebruikersgroep</span><span class="sxs-lookup"><span data-stu-id="39c2c-159">UserGroup</span></span> | <span data-ttu-id="39c2c-160">Server\_naam\\gebruiker\_groep</span><span class="sxs-lookup"><span data-stu-id="39c2c-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="39c2c-161">Localhost\\gebruiker\_groep</span><span class="sxs-lookup"><span data-stu-id="39c2c-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="39c2c-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="39c2c-162">.\\user\_group</span></span>
<span data-ttu-id="39c2c-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="39c2c-163">ComputerGroup</span></span> | <span data-ttu-id="39c2c-164">Server\_naam\\computer\_groep</span><span class="sxs-lookup"><span data-stu-id="39c2c-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="39c2c-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="39c2c-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="39c2c-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="39c2c-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="39c2c-167">Gatewayserver bevindt zich in een domein.</span><span class="sxs-lookup"><span data-stu-id="39c2c-167">Gateway server is in a domain</span></span>

<span data-ttu-id="39c2c-168">Parameter</span><span class="sxs-lookup"><span data-stu-id="39c2c-168">Parameter</span></span> | <span data-ttu-id="39c2c-169">Waarde</span><span class="sxs-lookup"><span data-stu-id="39c2c-169">Value</span></span>
-- | --
<span data-ttu-id="39c2c-170">Computernaam</span><span class="sxs-lookup"><span data-stu-id="39c2c-170">ComputerName</span></span> | <span data-ttu-id="39c2c-171">Volledig gekwalificeerde naam van gatewayserver of Localhost</span><span class="sxs-lookup"><span data-stu-id="39c2c-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="39c2c-172">Bestandsserver maakt deel uit van een werkgroep</span><span class="sxs-lookup"><span data-stu-id="39c2c-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="39c2c-173">Parameter</span><span class="sxs-lookup"><span data-stu-id="39c2c-173">Parameter</span></span> | <span data-ttu-id="39c2c-174">Waarde</span><span class="sxs-lookup"><span data-stu-id="39c2c-174">Value</span></span>
-- | --
<span data-ttu-id="39c2c-175">Computernaam</span><span class="sxs-lookup"><span data-stu-id="39c2c-175">ComputerName</span></span> | <span data-ttu-id="39c2c-176">Servernaam</span><span class="sxs-lookup"><span data-stu-id="39c2c-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="39c2c-177">Gatewayreferenties</span><span class="sxs-lookup"><span data-stu-id="39c2c-177">Gateway credentials</span></span>

<span data-ttu-id="39c2c-178">Meld u aan bij een gatewayserver als doelcomputer met referenties die de volgende indeling hebben.</span><span class="sxs-lookup"><span data-stu-id="39c2c-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="39c2c-179">Server\_naam\\gebruiker\_naam</span><span class="sxs-lookup"><span data-stu-id="39c2c-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="39c2c-180">Localhost\\gebruiker\_naam</span><span class="sxs-lookup"><span data-stu-id="39c2c-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="39c2c-181">. \\gebruiker\_naam</span><span class="sxs-lookup"><span data-stu-id="39c2c-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="39c2c-182">Een beveiligings-id (SID) wordt weergegeven in een autorisatieregel</span><span class="sxs-lookup"><span data-stu-id="39c2c-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="39c2c-183">Een beveiligings-id (SID) wordt weergegeven in een autorisatieregel in plaats van de syntaxis van de gebruiker\_naam en de computer\_naam.</span><span class="sxs-lookup"><span data-stu-id="39c2c-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="39c2c-184">De regel is niet meer geldig of de Active Directory Domain Services-query is mislukt.</span><span class="sxs-lookup"><span data-stu-id="39c2c-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="39c2c-185">Een autorisatieregel is doorgaans niet geldig in scenario's waarin de gatewayserver is in één keer in een werkgroep, maar later is toegevoegd aan een domein</span><span class="sxs-lookup"><span data-stu-id="39c2c-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="39c2c-186">Zich niet aanmelden met regel als een IPv6-adres met een domein</span><span class="sxs-lookup"><span data-stu-id="39c2c-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="39c2c-187">Kan niet aanmelden bij een doelcomputer die is opgegeven in autorisatieregels als een IPv6-adres met een domein.</span><span class="sxs-lookup"><span data-stu-id="39c2c-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="39c2c-188">Autorisatieregels ondersteunen geen IPv6-adressen in de vorm van een domeinnaam.</span><span class="sxs-lookup"><span data-stu-id="39c2c-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="39c2c-189">Als u een doelcomputer wilt opgeven met behulp van een IPv6-adres, gebruikt u het oorspronkelijke IPv6-adres (dat dubbele punten bevat) in de autorisatieregel.</span><span class="sxs-lookup"><span data-stu-id="39c2c-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="39c2c-190">Zowel het domein als numerieke (met dubbele punten) IPv6-adressen worden ondersteund als naam van de doelcomputer op de aanmeldingspagina van Windows PowerShell-webtoegang, maar niet in autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="39c2c-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="39c2c-191">Zie voor meer informatie over IPv6-adressen, [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="39c2c-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="39c2c-192">Zie ook</span><span class="sxs-lookup"><span data-stu-id="39c2c-192">See Also</span></span>

- <span data-ttu-id="39c2c-193">[Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="39c2c-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="39c2c-194">[De webgebaseerde Windows PowerShell-Console gebruiken](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="39c2c-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="39c2c-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="39c2c-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)