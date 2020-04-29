---
ms.date: 04/15/2020
keywords: Power shell, cmdlet
title: De tweede hop maken voor externe communicatie met PowerShell
ms.openlocfilehash: 7819058bd8118ba44e66ec658017f536076609b5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81527619"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="2252e-103">De tweede hop maken voor externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="2252e-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="2252e-104">Het ' tweede hop-probleem ' verwijst naar een situatie zoals de volgende:</span><span class="sxs-lookup"><span data-stu-id="2252e-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="2252e-105">U bent aangemeld bij _Servera_.</span><span class="sxs-lookup"><span data-stu-id="2252e-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="2252e-106">Vanuit _Servera_start u een externe Power shell-sessie om verbinding te maken met _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="2252e-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="2252e-107">Een opdracht die u uitvoert op _ServerB_ via uw externe Power shell-sessie probeert toegang te krijgen tot een resource op _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="2252e-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="2252e-108">De toegang tot de resource op _ServerC_ is geweigerd, omdat de referenties die u hebt gebruikt voor het maken van de externe Power shell-sessie niet zijn door gegeven van _ServerB_ naar _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="2252e-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="2252e-109">Er zijn verschillende manieren om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="2252e-109">There are several ways to address this problem.</span></span> <span data-ttu-id="2252e-110">In dit onderwerp bekijken we een aantal van de populairste oplossingen voor het probleem met de tweede hop.</span><span class="sxs-lookup"><span data-stu-id="2252e-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="2252e-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="2252e-111">CredSSP</span></span>

<span data-ttu-id="2252e-112">U kunt de [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) gebruiken voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="2252e-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="2252e-113">CredSSP slaat de referenties op de externe server (_ServerB_) op, zodat u hiermee wordt gebruikgemaakt van aanvallen op referentie diefstal.</span><span class="sxs-lookup"><span data-stu-id="2252e-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="2252e-114">Als de externe computer is aangetast, heeft de aanvaller toegang tot de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2252e-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="2252e-115">CredSSP is standaard uitgeschakeld op client-en Server computers.</span><span class="sxs-lookup"><span data-stu-id="2252e-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="2252e-116">U moet CredSSP alleen inschakelen in de meest vertrouwde omgevingen.</span><span class="sxs-lookup"><span data-stu-id="2252e-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="2252e-117">Bijvoorbeeld een domein beheerder die verbinding maakt met een domein controller omdat de domein controller zeer vertrouwd is.</span><span class="sxs-lookup"><span data-stu-id="2252e-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="2252e-118">Voor meer informatie over beveiligings problemen bij het gebruik van CredSSP voor externe communicatie met Power shell raadpleegt u [Accidental sabotage: wees op de hoogte van CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="2252e-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="2252e-119">Zie voor meer informatie over aanvallen op het weglaten van referentie dief stal [Pass-the-hash-aanvallen (PtH) en andere referentie diefstal](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="2252e-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="2252e-120">Voor een voor beeld van het inschakelen en gebruiken van CredSSP voor externe communicatie met Power shell, raadpleegt u [Power shell-functie voor tweede hop inschakelen met CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="2252e-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-121">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-121">Pros</span></span>

- <span data-ttu-id="2252e-122">Het werkt voor alle servers met Windows Server 2008 of hoger.</span><span class="sxs-lookup"><span data-stu-id="2252e-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-123">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-123">Cons</span></span>

- <span data-ttu-id="2252e-124">Bevat beveiligings problemen.</span><span class="sxs-lookup"><span data-stu-id="2252e-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="2252e-125">Vereist configuratie van de client-en Server functies.</span><span class="sxs-lookup"><span data-stu-id="2252e-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="2252e-126">Kerberos-overdracht (onbeperkt)</span><span class="sxs-lookup"><span data-stu-id="2252e-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="2252e-127">U kunt ook Kerberos-onbeperkte overdracht gebruiken om de tweede hop te maken.</span><span class="sxs-lookup"><span data-stu-id="2252e-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="2252e-128">Deze methode biedt echter geen controle over waar gedelegeerde referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2252e-128">However, this method provides no control of where delegated credentials are used.</span></span>

> [!NOTE]
> <span data-ttu-id="2252e-129">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="2252e-129">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2252e-130">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) en [Hulpprogram ma's en instellingen voor Kerberos-verificatie](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2252e-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx).</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-131">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-131">Pros</span></span>

- <span data-ttu-id="2252e-132">Vereist geen speciale code ring.</span><span class="sxs-lookup"><span data-stu-id="2252e-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-133">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-133">Cons</span></span>

- <span data-ttu-id="2252e-134">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="2252e-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2252e-135">Biedt geen controle over waar referenties worden gebruikt, waardoor een beveiligings probleem wordt opgelost.</span><span class="sxs-lookup"><span data-stu-id="2252e-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="2252e-136">Beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="2252e-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="2252e-137">U kunt verouderde, beperkte delegering (niet op basis van bronnen) gebruiken om de tweede hop te maken.</span><span class="sxs-lookup"><span data-stu-id="2252e-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="2252e-138">Configureer beperkte Kerberos-delegering met de optie elk verificatie protocol gebruiken om protocol overgang toe te staan.</span><span class="sxs-lookup"><span data-stu-id="2252e-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="2252e-139">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="2252e-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2252e-140">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) en [Hulpprogram ma's en instellingen voor Kerberos-verificatie](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2252e-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-141">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-141">Pros</span></span>

- <span data-ttu-id="2252e-142">Vereist geen speciale code ring</span><span class="sxs-lookup"><span data-stu-id="2252e-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-143">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-143">Cons</span></span>

- <span data-ttu-id="2252e-144">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="2252e-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2252e-145">Moet worden geconfigureerd op het Active Directory-object van de externe server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2252e-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="2252e-146">Beperkt tot één domein.</span><span class="sxs-lookup"><span data-stu-id="2252e-146">Limited to one domain.</span></span> <span data-ttu-id="2252e-147">Kan niet tussen domeinen of forests.</span><span class="sxs-lookup"><span data-stu-id="2252e-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="2252e-148">Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.</span><span class="sxs-lookup"><span data-stu-id="2252e-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="2252e-149">Op resources gebaseerde Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="2252e-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="2252e-150">Met behulp van beperkte Kerberos-delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het Server object waar de resources zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="2252e-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="2252e-151">In het tweede hop-scenario dat hierboven wordt beschreven, configureert u _ServerC_ om op te geven waar de gedelegeerde referenties worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="2252e-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="2252e-152">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="2252e-152">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2252e-153">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) en [Hulpprogram ma's en instellingen voor Kerberos-verificatie](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2252e-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-154">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-154">Pros</span></span>

- <span data-ttu-id="2252e-155">De referenties zijn niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2252e-155">Credentials are not stored.</span></span>
- <span data-ttu-id="2252e-156">Relatief eenvoudig te configureren met behulp van Power shell-cmdlets--geen speciale code ring vereist.</span><span class="sxs-lookup"><span data-stu-id="2252e-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="2252e-157">Er is geen speciale domein toegang vereist.</span><span class="sxs-lookup"><span data-stu-id="2252e-157">No special domain access is required.</span></span>
- <span data-ttu-id="2252e-158">Werkt in verschillende domeinen en forests.</span><span class="sxs-lookup"><span data-stu-id="2252e-158">Works across domains and forests.</span></span>
- <span data-ttu-id="2252e-159">Power shell-code.</span><span class="sxs-lookup"><span data-stu-id="2252e-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-160">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-160">Cons</span></span>

- <span data-ttu-id="2252e-161">Vereist Windows Server 2012 of hoger.</span><span class="sxs-lookup"><span data-stu-id="2252e-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="2252e-162">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="2252e-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2252e-163">Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.</span><span class="sxs-lookup"><span data-stu-id="2252e-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="2252e-164">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2252e-164">Example</span></span>

<span data-ttu-id="2252e-165">We kijken naar een Power shell-voor beeld dat op resources gebaseerde beperkte delegering op _ServerC_ zodanig configureert dat gedelegeerde referenties van een _ServerB_worden toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2252e-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="2252e-166">In dit voor beeld wordt ervan uitgegaan dat op alle servers Windows Server 2012 of hoger wordt uitgevoerd en dat er ten minste één domein controller met Windows Server 2012 elk domein is waarvan de servers deel uitmaken.</span><span class="sxs-lookup"><span data-stu-id="2252e-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="2252e-167">Voordat u beperkte delegering kunt configureren, moet u de `RSAT-AD-PowerShell` functie toevoegen om de Active Directory Power shell-module te installeren en deze module vervolgens in uw sessie te importeren:</span><span class="sxs-lookup"><span data-stu-id="2252e-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell
PS C:\> Import-Module ActiveDirectory
```

<span data-ttu-id="2252e-168">Verschillende beschik bare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** -para meter:</span><span class="sxs-lookup"><span data-stu-id="2252e-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="2252e-169">De para meter **PrincipalsAllowedToDelegateToAccount** stelt het Active Directory object kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**in dat een toegangs beheer lijst (ACL) bevat die aangeeft welke accounts machtigingen hebben voor het delegeren van referenties aan het gekoppelde account (in dit voor beeld is dit het computer account voor de _Server_).</span><span class="sxs-lookup"><span data-stu-id="2252e-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="2252e-170">We gaan nu de variabelen instellen die we gebruiken om de servers aan te duiden:</span><span class="sxs-lookup"><span data-stu-id="2252e-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="2252e-171">WinRM (en dus externe communicatie van Power shell) wordt standaard uitgevoerd als het computer account.</span><span class="sxs-lookup"><span data-stu-id="2252e-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="2252e-172">U kunt dit zien door te kijken naar de eigenschap **Start** naam van `winrm` de service:</span><span class="sxs-lookup"><span data-stu-id="2252e-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="2252e-173">Voor _ServerC_ om delegering vanuit een externe Power shell-sessie toe te staan op _ServerB_, wordt de toegang verleend door de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in te stellen op het computer object van _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="2252e-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="2252e-174">De Kerberos [-Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches weigert toegangs pogingen (negatieve cache) gedurende 15 minuten.</span><span class="sxs-lookup"><span data-stu-id="2252e-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="2252e-175">Als _ServerB_ eerder heeft geprobeerd toegang te krijgen tot _ServerC_, moet u de cache op _ServerB_ wissen door de volgende opdracht aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="2252e-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="2252e-176">U kunt de computer ook opnieuw opstarten of u moet ten minste 15 minuten wachten om de cache te wissen.</span><span class="sxs-lookup"><span data-stu-id="2252e-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="2252e-177">Nadat u de cache hebt gewist, kunt u code uitvoeren vanuit _Servera_ tot en met _ServerB_ tot _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="2252e-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="2252e-178">In dit voor beeld wordt `$using` de variabele gebruikt om de `$ServerC` variabele zichtbaar te maken voor _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="2252e-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="2252e-179">Zie about_Remote_Variables voor meer informatie `$using` over de variabele [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="2252e-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="2252e-180">Als u wilt toestaan dat meerdere servers referenties delegeren naar _ServerC_, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op een matrix:</span><span class="sxs-lookup"><span data-stu-id="2252e-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="2252e-181">Als u de tweede hop tussen domeinen wilt maken, voegt u een volledig gekwalificeerde domein naam (FQDN) toe van de domein controller van het domein waartoe _ServerB_ behoort:</span><span class="sxs-lookup"><span data-stu-id="2252e-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="2252e-182">Als u de bevoegdheid voor het delegeren van referenties wilt verwijderen naar ServerC, stelt u _ServerC_ de waarde `$null`van de para meter **PrincipalsAllowedToDelegateToAccount** op ServerC in op:</span><span class="sxs-lookup"><span data-stu-id="2252e-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="2252e-183">Informatie over op resources gebaseerde Kerberos-beperkte delegering</span><span class="sxs-lookup"><span data-stu-id="2252e-183">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="2252e-184">[Wat is nieuw in Kerberos-verificatie](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="2252e-184">[What's New in Kerberos Authentication](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11))</span></span>
- [<span data-ttu-id="2252e-185">Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 1, vereenvoudigt</span><span class="sxs-lookup"><span data-stu-id="2252e-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="2252e-186">Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 2, vereenvoudigt</span><span class="sxs-lookup"><span data-stu-id="2252e-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="2252e-187">Meer informatie over Kerberos-beperkte overdracht voor Azure Active Directory-toepassingsproxy-implementaties met geïntegreerde Windows-verificatie</span><span class="sxs-lookup"><span data-stu-id="2252e-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="2252e-188">[[MS-ADA2]: Active Directory schema kenmerken M 2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span><span class="sxs-lookup"><span data-stu-id="2252e-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="2252e-189">[[MS-SFU]: Kerberos protocol Extensions: Service for User en congebonden delegering Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span><span class="sxs-lookup"><span data-stu-id="2252e-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- [<span data-ttu-id="2252e-190">Extern beheer zonder beperkte delegering met behulp van PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="2252e-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](/archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="2252e-191">PSSessionConfiguration met behulp van runas</span><span class="sxs-lookup"><span data-stu-id="2252e-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="2252e-192">U kunt een sessie configuratie op _ServerB_ maken en de para meter **RunAsCredential** instellen.</span><span class="sxs-lookup"><span data-stu-id="2252e-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="2252e-193">Voor informatie over het gebruik van PSSessionConfiguration en Runas om het probleem met de tweede hop op te lossen, raadpleegt [u een andere oplossing voor externe communicatie met Power shell voor multi-hop](/archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting).</span><span class="sxs-lookup"><span data-stu-id="2252e-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](/archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting).</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-194">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-194">Pros</span></span>

- <span data-ttu-id="2252e-195">Werkt met een wille keurige server met WMF 3,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="2252e-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-196">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-196">Cons</span></span>

- <span data-ttu-id="2252e-197">Vereist de configuratie van **PSSessionConfiguration** en **runas** op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2252e-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="2252e-198">Vereist wachtwoord onderhoud bij gebruik van een **runas** -account van het domein</span><span class="sxs-lookup"><span data-stu-id="2252e-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="2252e-199">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="2252e-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="2252e-200">Met JEA kunt u de opdrachten die een beheerder tijdens een Power shell-sessie kan uitvoeren, beperken.</span><span class="sxs-lookup"><span data-stu-id="2252e-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="2252e-201">Het kan worden gebruikt om het probleem met de tweede hop op te lossen.</span><span class="sxs-lookup"><span data-stu-id="2252e-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="2252e-202">Zie [net genoeg beheer](/powershell/scripting/learn/remoting/jea/overview)voor meer informatie over jea.</span><span class="sxs-lookup"><span data-stu-id="2252e-202">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-203">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-203">Pros</span></span>

- <span data-ttu-id="2252e-204">Geen wachtwoord onderhoud wanneer een virtueel account wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2252e-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-205">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-205">Cons</span></span>

- <span data-ttu-id="2252e-206">Vereist WMF 5,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="2252e-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="2252e-207">Vereist configuratie op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2252e-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="2252e-208">Referenties binnen een invoke-opdracht-script blok door geven</span><span class="sxs-lookup"><span data-stu-id="2252e-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="2252e-209">U kunt referenties door geven binnen de para meter **script Block** van een aanroep naar de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="2252e-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="2252e-210">Voordelen</span><span class="sxs-lookup"><span data-stu-id="2252e-210">Pros</span></span>

- <span data-ttu-id="2252e-211">Vereist geen speciale server configuratie.</span><span class="sxs-lookup"><span data-stu-id="2252e-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="2252e-212">Werkt op elke server waarop WMF 2,0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2252e-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2252e-213">Nadelen</span><span class="sxs-lookup"><span data-stu-id="2252e-213">Cons</span></span>

- <span data-ttu-id="2252e-214">Hiervoor is een vreemd-code techniek vereist.</span><span class="sxs-lookup"><span data-stu-id="2252e-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="2252e-215">Bij het uitvoeren van WMF 2,0 is een andere syntaxis vereist voor het door geven van argumenten aan een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="2252e-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="2252e-216">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2252e-216">Example</span></span>

<span data-ttu-id="2252e-217">In het volgende voor beeld ziet u hoe de referenties worden door gegeven in een script blok voor de **opdracht invoke** :</span><span class="sxs-lookup"><span data-stu-id="2252e-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="2252e-218">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2252e-218">See also</span></span>

[<span data-ttu-id="2252e-219">Beveiligingsoverwegingen bij externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="2252e-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
