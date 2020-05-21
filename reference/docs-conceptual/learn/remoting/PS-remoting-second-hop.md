---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: De tweede hop maken voor externe communicatie met PowerShell
ms.openlocfilehash: 3a9db11726d4c02dc69e52c45da304f7422def39
ms.sourcegitcommit: 843756c8277e7afb874867703963248abc8a6c91
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83439373"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="20d4d-103">De tweede hop maken voor externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="20d4d-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="20d4d-104">Het ' tweede hop-probleem ' verwijst naar een situatie zoals de volgende:</span><span class="sxs-lookup"><span data-stu-id="20d4d-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="20d4d-105">U bent aangemeld bij _Servera_.</span><span class="sxs-lookup"><span data-stu-id="20d4d-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="20d4d-106">Vanuit _Servera_start u een externe Power shell-sessie om verbinding te maken met _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="20d4d-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="20d4d-107">Een opdracht die u uitvoert op _ServerB_ via uw externe Power shell-sessie probeert toegang te krijgen tot een resource op _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="20d4d-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="20d4d-108">De toegang tot de resource op _ServerC_ is geweigerd, omdat de referenties die u hebt gebruikt voor het maken van de externe Power shell-sessie niet zijn door gegeven van _ServerB_ naar _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="20d4d-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="20d4d-109">Er zijn verschillende manieren om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-109">There are several ways to address this problem.</span></span> <span data-ttu-id="20d4d-110">De volgende tabel bevat de methoden in volg orde van voor keur.</span><span class="sxs-lookup"><span data-stu-id="20d4d-110">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="20d4d-111">Configuratie</span><span class="sxs-lookup"><span data-stu-id="20d4d-111">Configuration</span></span>                       |                                  <span data-ttu-id="20d4d-112">Notitie</span><span class="sxs-lookup"><span data-stu-id="20d4d-112">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="20d4d-113">CredSSP</span><span class="sxs-lookup"><span data-stu-id="20d4d-113">CredSSP</span></span>                                                  | <span data-ttu-id="20d4d-114">Het gebruiks gemak en de beveiliging</span><span class="sxs-lookup"><span data-stu-id="20d4d-114">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="20d4d-115">Op resources gebaseerde Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="20d4d-115">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="20d4d-116">Betere beveiliging met een eenvoudigere configuratie</span><span class="sxs-lookup"><span data-stu-id="20d4d-116">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="20d4d-117">Beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="20d4d-117">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="20d4d-118">Hoge beveiliging, maar vereist domein beheerder</span><span class="sxs-lookup"><span data-stu-id="20d4d-118">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="20d4d-119">Kerberos-overdracht (onbeperkt)</span><span class="sxs-lookup"><span data-stu-id="20d4d-119">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="20d4d-120">Niet aanbevolen</span><span class="sxs-lookup"><span data-stu-id="20d4d-120">Not recommended</span></span>                                                        |
| <span data-ttu-id="20d4d-121">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="20d4d-121">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="20d4d-122">Kan de beste beveiliging bieden, maar vereist een gedetailleerdere configuratie</span><span class="sxs-lookup"><span data-stu-id="20d4d-122">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="20d4d-123">PSSessionConfiguration met behulp van runas</span><span class="sxs-lookup"><span data-stu-id="20d4d-123">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="20d4d-124">Eenvoudiger te configureren, maar vereist referentie beheer</span><span class="sxs-lookup"><span data-stu-id="20d4d-124">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="20d4d-125">Referenties in een `Invoke-Command` script blok door geven</span><span class="sxs-lookup"><span data-stu-id="20d4d-125">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="20d4d-126">Eenvoudig te gebruiken, maar u moet referenties opgeven</span><span class="sxs-lookup"><span data-stu-id="20d4d-126">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="20d4d-127">CredSSP</span><span class="sxs-lookup"><span data-stu-id="20d4d-127">CredSSP</span></span>

<span data-ttu-id="20d4d-128">U kunt de [Credential Security Support Provider (CredSSP)][credssp] gebruiken voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="20d4d-128">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="20d4d-129">CredSSP slaat de referenties op de externe server (_ServerB_) op, zodat u hiermee wordt gebruikgemaakt van aanvallen op referentie diefstal.</span><span class="sxs-lookup"><span data-stu-id="20d4d-129">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="20d4d-130">Als de externe computer is aangetast, heeft de aanvaller toegang tot de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="20d4d-130">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="20d4d-131">CredSSP is standaard uitgeschakeld op client-en Server computers.</span><span class="sxs-lookup"><span data-stu-id="20d4d-131">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="20d4d-132">U moet CredSSP alleen inschakelen in de meest vertrouwde omgevingen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-132">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="20d4d-133">Bijvoorbeeld een domein beheerder die verbinding maakt met een domein controller omdat de domein controller zeer vertrouwd is.</span><span class="sxs-lookup"><span data-stu-id="20d4d-133">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="20d4d-134">Voor meer informatie over beveiligings problemen bij het gebruik van CredSSP voor externe communicatie met Power shell raadpleegt u [Accidental sabotage: wees op de hoogte van CredSSP][beware].</span><span class="sxs-lookup"><span data-stu-id="20d4d-134">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="20d4d-135">Zie voor meer informatie over aanvallen op het weglaten van referentie dief stal [Pass-the-hash-aanvallen (PtH) en andere referentie diefstal][pth].</span><span class="sxs-lookup"><span data-stu-id="20d4d-135">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="20d4d-136">Voor een voor beeld van het inschakelen en gebruiken van CredSSP voor externe communicatie met Power shell, raadpleegt u [Power shell-functie voor tweede hop inschakelen met CredSSP][credssp-psblog].</span><span class="sxs-lookup"><span data-stu-id="20d4d-136">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="20d4d-137">**-Professionals**</span><span class="sxs-lookup"><span data-stu-id="20d4d-137">**Pros**</span></span>

- <span data-ttu-id="20d4d-138">Het werkt voor alle servers met Windows Server 2008 of hoger.</span><span class="sxs-lookup"><span data-stu-id="20d4d-138">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="20d4d-139">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="20d4d-139">**Cons**</span></span>

- <span data-ttu-id="20d4d-140">Bevat beveiligings problemen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-140">Has security vulnerabilities.</span></span>
- <span data-ttu-id="20d4d-141">Vereist configuratie van de client-en Server functies.</span><span class="sxs-lookup"><span data-stu-id="20d4d-141">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="20d4d-142">Werkt niet met de groep met beveiligde gebruikers.</span><span class="sxs-lookup"><span data-stu-id="20d4d-142">Does not work with the Protected Users group.</span></span> <span data-ttu-id="20d4d-143">Zie voor meer informatie [beveiligings groep voor beveiligde gebruikers][protected-users].</span><span class="sxs-lookup"><span data-stu-id="20d4d-143">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="20d4d-144">Beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="20d4d-144">Kerberos constrained delegation</span></span>

<span data-ttu-id="20d4d-145">U kunt verouderde, beperkte delegering (niet op basis van bronnen) gebruiken om de tweede hop te maken.</span><span class="sxs-lookup"><span data-stu-id="20d4d-145">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="20d4d-146">Configureer beperkte Kerberos-delegering met de optie elk verificatie protocol gebruiken om protocol overgang toe te staan.</span><span class="sxs-lookup"><span data-stu-id="20d4d-146">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="20d4d-147">**-Professionals**</span><span class="sxs-lookup"><span data-stu-id="20d4d-147">**Pros**</span></span>

- <span data-ttu-id="20d4d-148">Vereist geen speciale code ring</span><span class="sxs-lookup"><span data-stu-id="20d4d-148">Requires no special coding</span></span>
- <span data-ttu-id="20d4d-149">De referenties zijn niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-149">Credentials are not stored.</span></span>

<span data-ttu-id="20d4d-150">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="20d4d-150">**Cons**</span></span>

- <span data-ttu-id="20d4d-151">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="20d4d-151">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="20d4d-152">Vereist dat domein beheerder toegang heeft om te configureren.</span><span class="sxs-lookup"><span data-stu-id="20d4d-152">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="20d4d-153">Moet worden geconfigureerd op het Active Directory-object van de externe server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="20d4d-153">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="20d4d-154">Beperkt tot één domein.</span><span class="sxs-lookup"><span data-stu-id="20d4d-154">Limited to one domain.</span></span> <span data-ttu-id="20d4d-155">Kan niet tussen domeinen of forests.</span><span class="sxs-lookup"><span data-stu-id="20d4d-155">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="20d4d-156">Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.</span><span class="sxs-lookup"><span data-stu-id="20d4d-156">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="20d4d-157">U kunt met _ServerB_ een Kerberos-ticket verkrijgen voor _ServerC_ namens de gebruiker zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="20d4d-157">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="20d4d-158">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="20d4d-158">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="20d4d-159">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts][blog] en [Hulpprogram ma's en instellingen voor Kerberos-verificatie][ktools]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="20d4d-159">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="20d4d-160">Op resources gebaseerde Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="20d4d-160">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="20d4d-161">Met behulp van beperkte Kerberos-delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het Server object waar de resources zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="20d4d-161">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="20d4d-162">In het tweede hop-scenario dat hierboven wordt beschreven, configureert u _ServerC_ om op te geven waar de gedelegeerde referenties worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="20d4d-162">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="20d4d-163">**-Professionals**</span><span class="sxs-lookup"><span data-stu-id="20d4d-163">**Pros**</span></span>

- <span data-ttu-id="20d4d-164">De referenties zijn niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-164">Credentials are not stored.</span></span>
- <span data-ttu-id="20d4d-165">Geconfigureerd met Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="20d4d-165">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="20d4d-166">Er is geen speciale code vereist.</span><span class="sxs-lookup"><span data-stu-id="20d4d-166">No special coding required.</span></span>
- <span data-ttu-id="20d4d-167">Vereist geen domein beheerders toegang om te configureren.</span><span class="sxs-lookup"><span data-stu-id="20d4d-167">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="20d4d-168">Werkt in verschillende domeinen en forests.</span><span class="sxs-lookup"><span data-stu-id="20d4d-168">Works across domains and forests.</span></span>

<span data-ttu-id="20d4d-169">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="20d4d-169">**Cons**</span></span>

- <span data-ttu-id="20d4d-170">Vereist Windows Server 2012 of hoger.</span><span class="sxs-lookup"><span data-stu-id="20d4d-170">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="20d4d-171">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="20d4d-171">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="20d4d-172">Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.</span><span class="sxs-lookup"><span data-stu-id="20d4d-172">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="20d4d-173">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="20d4d-173">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="20d4d-174">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts][blog] en [Hulpprogram ma's en instellingen voor Kerberos-verificatie][ktools]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="20d4d-174">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="20d4d-175">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="20d4d-175">Example</span></span>

<span data-ttu-id="20d4d-176">Laten we eens kijken naar een Power shell-voor beeld voor het configureren van beperkte delegering op basis van resources op _ServerC_ om gedelegeerde referenties van een _ServerB_toe te staan.</span><span class="sxs-lookup"><span data-stu-id="20d4d-176">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="20d4d-177">In dit voor beeld wordt ervan uitgegaan dat op alle servers Windows Server 2012 of hoger wordt uitgevoerd en dat er ten minste één domein controller met Windows Server 2012 elk domein is waarvan de servers deel uitmaken.</span><span class="sxs-lookup"><span data-stu-id="20d4d-177">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="20d4d-178">Voordat u beperkte delegering kunt configureren, moet u de `RSAT-AD-PowerShell` functie toevoegen om de Active Directory Power shell-module te installeren en deze module vervolgens in uw sessie te importeren:</span><span class="sxs-lookup"><span data-stu-id="20d4d-178">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="20d4d-179">Verschillende beschik bare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** -para meter:</span><span class="sxs-lookup"><span data-stu-id="20d4d-179">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="20d4d-180">De para meter **PrincipalsAllowedToDelegateToAccount** stelt het Active Directory object kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**in dat een toegangs beheer lijst (ACL) bevat die aangeeft welke accounts machtigingen hebben voor het delegeren van referenties aan het gekoppelde account (in dit voor beeld is dit het computer account voor _Servera_).</span><span class="sxs-lookup"><span data-stu-id="20d4d-180">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_).</span></span>

<span data-ttu-id="20d4d-181">We gaan nu de variabelen instellen die we gebruiken om de servers aan te duiden:</span><span class="sxs-lookup"><span data-stu-id="20d4d-181">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="20d4d-182">WinRM (en dus externe communicatie van Power shell) wordt standaard uitgevoerd als het computer account.</span><span class="sxs-lookup"><span data-stu-id="20d4d-182">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="20d4d-183">U kunt dit zien door te kijken naar de eigenschap **Start** naam van de `winrm` service:</span><span class="sxs-lookup"><span data-stu-id="20d4d-183">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="20d4d-184">Voor _ServerC_ voor het toestaan van delegering vanuit een externe Power shell-sessie op _ServerB_, moeten we de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ instellen op het computer object van _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="20d4d-184">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="20d4d-185">De Kerberos- [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches geweigerd-toegangs pogingen (negatieve cache) gedurende 15 minuten.</span><span class="sxs-lookup"><span data-stu-id="20d4d-185">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="20d4d-186">Als _ServerB_ eerder heeft geprobeerd toegang te krijgen tot _ServerC_, moet u de cache op _ServerB_ wissen door de volgende opdracht aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="20d4d-186">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="20d4d-187">U kunt de computer ook opnieuw opstarten of u moet ten minste 15 minuten wachten om de cache te wissen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-187">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="20d4d-188">Nadat u de cache hebt gewist, kunt u code uitvoeren vanuit _Servera_ tot en met _ServerB_ tot _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="20d4d-188">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="20d4d-189">In dit voor beeld `$using` wordt de variabele gebruikt om de `$ServerC` variabele zichtbaar te maken voor _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="20d4d-189">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="20d4d-190">Zie about_Remote_Variables voor meer informatie over de `$using` variabele [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span><span class="sxs-lookup"><span data-stu-id="20d4d-190">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="20d4d-191">Als u wilt toestaan dat meerdere servers referenties delegeren naar _ServerC_, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op een matrix:</span><span class="sxs-lookup"><span data-stu-id="20d4d-191">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="20d4d-192">Als u de tweede hop tussen domeinen wilt maken, voegt u een volledig gekwalificeerde domein naam (FQDN) toe van de domein controller van het domein waartoe _ServerB_ behoort:</span><span class="sxs-lookup"><span data-stu-id="20d4d-192">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="20d4d-193">Als u de bevoegdheid voor het delegeren van referenties wilt verwijderen naar ServerC, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op `$null` :</span><span class="sxs-lookup"><span data-stu-id="20d4d-193">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="20d4d-194">Informatie over op resources gebaseerde Kerberos-beperkte delegering</span><span class="sxs-lookup"><span data-stu-id="20d4d-194">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="20d4d-195">[Wat is nieuw in Kerberos-verificatie][whats-new]</span><span class="sxs-lookup"><span data-stu-id="20d4d-195">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="20d4d-196">[Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 1, vereenvoudigt][kcd2012-1]</span><span class="sxs-lookup"><span data-stu-id="20d4d-196">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="20d4d-197">[Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 2, vereenvoudigt][kcd2012-2]</span><span class="sxs-lookup"><span data-stu-id="20d4d-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="20d4d-198">[Meer informatie over Kerberos-beperkte overdracht voor Azure Active Directory-toepassingsproxy-implementaties met geïntegreerde Windows-verificatie][kcdpaper]</span><span class="sxs-lookup"><span data-stu-id="20d4d-198">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="20d4d-199">[[MS-ADA2] Active Directory schema kenmerken M 2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span><span class="sxs-lookup"><span data-stu-id="20d4d-199">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="20d4d-200">[[MS-SFU] Kerberos-protocol uitbreidingen: service voor gebruiker en beperkt delegering Protocol 1.3.2 S4U2proxy][MS-SFU]</span><span class="sxs-lookup"><span data-stu-id="20d4d-200">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="20d4d-201">[Extern beheer zonder beperkte delegering met behulp van PrincipalsAllowedToDelegateToAccount][remote-admin]</span><span class="sxs-lookup"><span data-stu-id="20d4d-201">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="20d4d-202">Kerberos-overdracht (onbeperkt)</span><span class="sxs-lookup"><span data-stu-id="20d4d-202">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="20d4d-203">U kunt ook Kerberos-onbeperkte overdracht gebruiken om de tweede hop te maken.</span><span class="sxs-lookup"><span data-stu-id="20d4d-203">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="20d4d-204">Net als alle Kerberos-scenario's worden referenties niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-204">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="20d4d-205">Deze methode biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="20d4d-205">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="20d4d-206">Deze methode biedt geen controle over waar gedelegeerde referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="20d4d-206">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="20d4d-207">Het is minder veilig dan CredSSP.</span><span class="sxs-lookup"><span data-stu-id="20d4d-207">It is less secure than CredSSP.</span></span> <span data-ttu-id="20d4d-208">Deze methode mag alleen worden gebruikt voor test scenario's.</span><span class="sxs-lookup"><span data-stu-id="20d4d-208">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="20d4d-209">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="20d4d-209">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="20d4d-210">Met JEA kunt u de opdrachten die een beheerder tijdens een Power shell-sessie kan uitvoeren, beperken.</span><span class="sxs-lookup"><span data-stu-id="20d4d-210">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="20d4d-211">Het kan worden gebruikt om het probleem met de tweede hop op te lossen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-211">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="20d4d-212">Zie [net genoeg beheer](/powershell/scripting/learn/remoting/jea/overview)voor meer informatie over jea.</span><span class="sxs-lookup"><span data-stu-id="20d4d-212">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="20d4d-213">**-Professionals**</span><span class="sxs-lookup"><span data-stu-id="20d4d-213">**Pros**</span></span>

- <span data-ttu-id="20d4d-214">Geen wachtwoord onderhoud wanneer een virtueel account wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="20d4d-214">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="20d4d-215">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="20d4d-215">**Cons**</span></span>

- <span data-ttu-id="20d4d-216">Vereist WMF 5,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="20d4d-216">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="20d4d-217">Vereist configuratie op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="20d4d-217">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="20d4d-218">PSSessionConfiguration met behulp van runas</span><span class="sxs-lookup"><span data-stu-id="20d4d-218">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="20d4d-219">U kunt een sessie configuratie op _ServerB_ maken en de para meter **RunAsCredential** instellen.</span><span class="sxs-lookup"><span data-stu-id="20d4d-219">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="20d4d-220">Voor informatie over het gebruik van **PSSessionConfiguration** en **runas** om het probleem met de tweede hop op te lossen, raadpleegt [u een andere oplossing voor externe communicatie met Power shell voor multi-hop][pssessionconfig].</span><span class="sxs-lookup"><span data-stu-id="20d4d-220">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="20d4d-221">**-Professionals**</span><span class="sxs-lookup"><span data-stu-id="20d4d-221">**Pros**</span></span>

- <span data-ttu-id="20d4d-222">Werkt met een wille keurige server met WMF 3,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="20d4d-222">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="20d4d-223">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="20d4d-223">**Cons**</span></span>

- <span data-ttu-id="20d4d-224">Vereist de configuratie van **PSSessionConfiguration** en **runas** op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="20d4d-224">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="20d4d-225">Vereist wachtwoord onderhoud bij gebruik van een **runas** -account van het domein</span><span class="sxs-lookup"><span data-stu-id="20d4d-225">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="20d4d-226">Referenties binnen een invoke-opdracht-script blok door geven</span><span class="sxs-lookup"><span data-stu-id="20d4d-226">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="20d4d-227">U kunt referenties door geven binnen de para meter **script Block** van een aanroep naar de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="20d4d-227">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="20d4d-228">**-Professionals**</span><span class="sxs-lookup"><span data-stu-id="20d4d-228">**Pros**</span></span>

- <span data-ttu-id="20d4d-229">Vereist geen speciale server configuratie.</span><span class="sxs-lookup"><span data-stu-id="20d4d-229">Does not require special server configuration.</span></span>
- <span data-ttu-id="20d4d-230">Werkt op elke server waarop WMF 2,0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="20d4d-230">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="20d4d-231">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="20d4d-231">**Cons**</span></span>

- <span data-ttu-id="20d4d-232">Hiervoor is een vreemd-code techniek vereist.</span><span class="sxs-lookup"><span data-stu-id="20d4d-232">Requires an awkward code technique.</span></span>
- <span data-ttu-id="20d4d-233">Bij het uitvoeren van WMF 2,0 is een andere syntaxis vereist voor het door geven van argumenten aan een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="20d4d-233">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="20d4d-234">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="20d4d-234">Example</span></span>

<span data-ttu-id="20d4d-235">In het volgende voor beeld ziet u hoe de referenties worden door gegeven in een script blok voor de **opdracht invoke** :</span><span class="sxs-lookup"><span data-stu-id="20d4d-235">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="20d4d-236">Zie ook</span><span class="sxs-lookup"><span data-stu-id="20d4d-236">See also</span></span>

[<span data-ttu-id="20d4d-237">Beveiligingsoverwegingen bij externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="20d4d-237">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
