---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: De tweede hop maken voor externe communicatie met PowerShell
description: In dit artikel worden de verschillende methoden beschreven voor het configureren van de tweede hop-verificatie voor externe communicatie met Power shell, met inbegrip van de beveiligings implicaties en aanbevelingen.
ms.openlocfilehash: 905b27b4e6c612249c945a741bbe0d2ba9ae28aa
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501368"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="382eb-104">De tweede hop maken voor externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="382eb-104">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="382eb-105">Het ' tweede hop-probleem ' verwijst naar een situatie zoals de volgende:</span><span class="sxs-lookup"><span data-stu-id="382eb-105">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="382eb-106">U bent aangemeld bij _Servera_.</span><span class="sxs-lookup"><span data-stu-id="382eb-106">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="382eb-107">Vanuit _Servera_start u een externe Power shell-sessie om verbinding te maken met _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="382eb-107">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="382eb-108">Een opdracht die u uitvoert op _ServerB_ via uw externe Power shell-sessie probeert toegang te krijgen tot een resource op _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="382eb-108">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="382eb-109">De toegang tot de resource op _ServerC_ is geweigerd, omdat de referenties die u hebt gebruikt voor het maken van de externe Power shell-sessie niet zijn door gegeven van _ServerB_ naar _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="382eb-109">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="382eb-110">Er zijn verschillende manieren om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="382eb-110">There are several ways to address this problem.</span></span> <span data-ttu-id="382eb-111">De volgende tabel bevat de methoden in volg orde van voor keur.</span><span class="sxs-lookup"><span data-stu-id="382eb-111">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="382eb-112">Configuratie</span><span class="sxs-lookup"><span data-stu-id="382eb-112">Configuration</span></span>                       |                                  <span data-ttu-id="382eb-113">Notitie</span><span class="sxs-lookup"><span data-stu-id="382eb-113">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="382eb-114">CredSSP</span><span class="sxs-lookup"><span data-stu-id="382eb-114">CredSSP</span></span>                                                  | <span data-ttu-id="382eb-115">Het gebruiks gemak en de beveiliging</span><span class="sxs-lookup"><span data-stu-id="382eb-115">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="382eb-116">Op resources gebaseerde Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="382eb-116">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="382eb-117">Betere beveiliging met een eenvoudigere configuratie</span><span class="sxs-lookup"><span data-stu-id="382eb-117">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="382eb-118">Beperkte Kerberos-delegering</span><span class="sxs-lookup"><span data-stu-id="382eb-118">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="382eb-119">Hoge beveiliging, maar vereist domein beheerder</span><span class="sxs-lookup"><span data-stu-id="382eb-119">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="382eb-120">Kerberos-overdracht (onbeperkt)</span><span class="sxs-lookup"><span data-stu-id="382eb-120">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="382eb-121">Niet aanbevolen</span><span class="sxs-lookup"><span data-stu-id="382eb-121">Not recommended</span></span>                                                        |
| <span data-ttu-id="382eb-122">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="382eb-122">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="382eb-123">Kan de beste beveiliging bieden, maar vereist een gedetailleerdere configuratie</span><span class="sxs-lookup"><span data-stu-id="382eb-123">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="382eb-124">PSSessionConfiguration met behulp van runas</span><span class="sxs-lookup"><span data-stu-id="382eb-124">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="382eb-125">Eenvoudiger te configureren, maar vereist referentie beheer</span><span class="sxs-lookup"><span data-stu-id="382eb-125">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="382eb-126">Referenties in een `Invoke-Command` script blok door geven</span><span class="sxs-lookup"><span data-stu-id="382eb-126">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="382eb-127">Eenvoudig te gebruiken, maar u moet referenties opgeven</span><span class="sxs-lookup"><span data-stu-id="382eb-127">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="382eb-128">CredSSP</span><span class="sxs-lookup"><span data-stu-id="382eb-128">CredSSP</span></span>

<span data-ttu-id="382eb-129">U kunt de [Credential Security Support Provider (CredSSP)][credssp] gebruiken voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="382eb-129">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="382eb-130">CredSSP slaat de referenties op de externe server (_ServerB_) op, zodat u hiermee wordt gebruikgemaakt van aanvallen op referentie diefstal.</span><span class="sxs-lookup"><span data-stu-id="382eb-130">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="382eb-131">Als de externe computer is aangetast, heeft de aanvaller toegang tot de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="382eb-131">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="382eb-132">CredSSP is standaard uitgeschakeld op client-en Server computers.</span><span class="sxs-lookup"><span data-stu-id="382eb-132">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="382eb-133">U moet CredSSP alleen inschakelen in de meest vertrouwde omgevingen.</span><span class="sxs-lookup"><span data-stu-id="382eb-133">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="382eb-134">Bijvoorbeeld een domein beheerder die verbinding maakt met een domein controller omdat de domein controller zeer vertrouwd is.</span><span class="sxs-lookup"><span data-stu-id="382eb-134">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="382eb-135">Voor meer informatie over beveiligings problemen bij het gebruik van CredSSP voor externe communicatie met Power shell raadpleegt u [Accidental sabotage: wees op de hoogte van CredSSP][beware].</span><span class="sxs-lookup"><span data-stu-id="382eb-135">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="382eb-136">Zie voor meer informatie over aanvallen op het weglaten van referentie dief stal [Pass-the-hash-aanvallen (PtH) en andere referentie diefstal][pth].</span><span class="sxs-lookup"><span data-stu-id="382eb-136">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="382eb-137">Voor een voor beeld van het inschakelen en gebruiken van CredSSP voor externe communicatie met Power shell, raadpleegt u [Power shell-functie voor tweede hop inschakelen met CredSSP][credssp-psblog].</span><span class="sxs-lookup"><span data-stu-id="382eb-137">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="382eb-138">**Voordelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-138">**Pros**</span></span>

- <span data-ttu-id="382eb-139">Het werkt voor alle servers met Windows Server 2008 of hoger.</span><span class="sxs-lookup"><span data-stu-id="382eb-139">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="382eb-140">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-140">**Cons**</span></span>

- <span data-ttu-id="382eb-141">Bevat beveiligings problemen.</span><span class="sxs-lookup"><span data-stu-id="382eb-141">Has security vulnerabilities.</span></span>
- <span data-ttu-id="382eb-142">Vereist configuratie van de client-en Server functies.</span><span class="sxs-lookup"><span data-stu-id="382eb-142">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="382eb-143">Werkt niet met de groep met beveiligde gebruikers.</span><span class="sxs-lookup"><span data-stu-id="382eb-143">Does not work with the Protected Users group.</span></span> <span data-ttu-id="382eb-144">Zie voor meer informatie [beveiligings groep voor beveiligde gebruikers][protected-users].</span><span class="sxs-lookup"><span data-stu-id="382eb-144">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="382eb-145">Beperkte Kerberos-delegering</span><span class="sxs-lookup"><span data-stu-id="382eb-145">Kerberos constrained delegation</span></span>

<span data-ttu-id="382eb-146">U kunt verouderde, beperkte delegering (niet op basis van bronnen) gebruiken om de tweede hop te maken.</span><span class="sxs-lookup"><span data-stu-id="382eb-146">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="382eb-147">Configureer beperkte Kerberos-delegering met de optie elk verificatie protocol gebruiken om protocol overgang toe te staan.</span><span class="sxs-lookup"><span data-stu-id="382eb-147">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="382eb-148">**Voordelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-148">**Pros**</span></span>

- <span data-ttu-id="382eb-149">Vereist geen speciale code ring</span><span class="sxs-lookup"><span data-stu-id="382eb-149">Requires no special coding</span></span>
- <span data-ttu-id="382eb-150">De referenties zijn niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="382eb-150">Credentials are not stored.</span></span>

<span data-ttu-id="382eb-151">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-151">**Cons**</span></span>

- <span data-ttu-id="382eb-152">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="382eb-152">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="382eb-153">Vereist dat domein beheerder toegang heeft om te configureren.</span><span class="sxs-lookup"><span data-stu-id="382eb-153">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="382eb-154">Moet worden geconfigureerd op het Active Directory-object van de externe server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="382eb-154">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="382eb-155">Beperkt tot één domein.</span><span class="sxs-lookup"><span data-stu-id="382eb-155">Limited to one domain.</span></span> <span data-ttu-id="382eb-156">Kan niet tussen domeinen of forests.</span><span class="sxs-lookup"><span data-stu-id="382eb-156">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="382eb-157">Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.</span><span class="sxs-lookup"><span data-stu-id="382eb-157">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="382eb-158">U kunt met _ServerB_ een Kerberos-ticket verkrijgen voor _ServerC_ namens de gebruiker zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="382eb-158">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="382eb-159">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="382eb-159">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="382eb-160">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts][blog] en [Hulpprogram ma's en instellingen voor Kerberos-verificatie][ktools]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="382eb-160">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="382eb-161">Op resources gebaseerde Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="382eb-161">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="382eb-162">Met behulp van beperkte Kerberos-delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het Server object waar de resources zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="382eb-162">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="382eb-163">In het tweede hop-scenario dat hierboven wordt beschreven, configureert u _ServerC_ om op te geven waar de gedelegeerde referenties worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="382eb-163">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="382eb-164">**Voordelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-164">**Pros**</span></span>

- <span data-ttu-id="382eb-165">De referenties zijn niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="382eb-165">Credentials are not stored.</span></span>
- <span data-ttu-id="382eb-166">Geconfigureerd met Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="382eb-166">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="382eb-167">Er is geen speciale code vereist.</span><span class="sxs-lookup"><span data-stu-id="382eb-167">No special coding required.</span></span>
- <span data-ttu-id="382eb-168">Vereist geen domein beheerders toegang om te configureren.</span><span class="sxs-lookup"><span data-stu-id="382eb-168">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="382eb-169">Werkt in verschillende domeinen en forests.</span><span class="sxs-lookup"><span data-stu-id="382eb-169">Works across domains and forests.</span></span>

<span data-ttu-id="382eb-170">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-170">**Cons**</span></span>

- <span data-ttu-id="382eb-171">Vereist Windows Server 2012 of hoger.</span><span class="sxs-lookup"><span data-stu-id="382eb-171">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="382eb-172">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="382eb-172">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="382eb-173">Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.</span><span class="sxs-lookup"><span data-stu-id="382eb-173">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="382eb-174">Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="382eb-174">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="382eb-175">Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts][blog] en [Hulpprogram ma's en instellingen voor Kerberos-verificatie][ktools]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="382eb-175">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="382eb-176">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="382eb-176">Example</span></span>

<span data-ttu-id="382eb-177">Laten we eens kijken naar een Power shell-voor beeld voor het configureren van beperkte delegering op basis van resources op _ServerC_ om gedelegeerde referenties van een _ServerB_toe te staan.</span><span class="sxs-lookup"><span data-stu-id="382eb-177">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="382eb-178">In dit voor beeld wordt ervan uitgegaan dat op alle servers Windows Server 2012 of hoger wordt uitgevoerd en dat er ten minste één domein controller met Windows Server 2012 elk domein is waarvan de servers deel uitmaken.</span><span class="sxs-lookup"><span data-stu-id="382eb-178">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="382eb-179">Voordat u beperkte delegering kunt configureren, moet u de `RSAT-AD-PowerShell` functie toevoegen om de Active Directory Power shell-module te installeren en deze module vervolgens in uw sessie te importeren:</span><span class="sxs-lookup"><span data-stu-id="382eb-179">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="382eb-180">Verschillende beschik bare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** -para meter:</span><span class="sxs-lookup"><span data-stu-id="382eb-180">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="382eb-181">De para meter **PrincipalsAllowedToDelegateToAccount** stelt het Active Directory object kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**in dat een toegangs beheer lijst (ACL) bevat die aangeeft welke accounts machtigingen hebben voor het delegeren van referenties aan het gekoppelde account (in dit voor beeld is dit het computer account voor _Servera_).</span><span class="sxs-lookup"><span data-stu-id="382eb-181">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_).</span></span>

<span data-ttu-id="382eb-182">We gaan nu de variabelen instellen die we gebruiken om de servers aan te duiden:</span><span class="sxs-lookup"><span data-stu-id="382eb-182">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="382eb-183">WinRM (en dus externe communicatie van Power shell) wordt standaard uitgevoerd als het computer account.</span><span class="sxs-lookup"><span data-stu-id="382eb-183">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="382eb-184">U kunt dit zien door te kijken naar de eigenschap **Start** naam van de `winrm` service:</span><span class="sxs-lookup"><span data-stu-id="382eb-184">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="382eb-185">Voor _ServerC_ voor het toestaan van delegering vanuit een externe Power shell-sessie op _ServerB_, moeten we de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ instellen op het computer object van _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="382eb-185">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="382eb-186">De Kerberos- [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches geweigerd-toegangs pogingen (negatieve cache) gedurende 15 minuten.</span><span class="sxs-lookup"><span data-stu-id="382eb-186">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="382eb-187">Als _ServerB_ eerder heeft geprobeerd toegang te krijgen tot _ServerC_, moet u de cache op _ServerB_ wissen door de volgende opdracht aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="382eb-187">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="382eb-188">U kunt de computer ook opnieuw opstarten of u moet ten minste 15 minuten wachten om de cache te wissen.</span><span class="sxs-lookup"><span data-stu-id="382eb-188">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="382eb-189">Nadat u de cache hebt gewist, kunt u code uitvoeren vanuit _Servera_ tot en met _ServerB_ tot _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="382eb-189">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="382eb-190">In dit voor beeld `$using` wordt de variabele gebruikt om de `$ServerC` variabele zichtbaar te maken voor _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="382eb-190">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="382eb-191">Zie about_Remote_Variables voor meer informatie over de `$using` variabele [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span><span class="sxs-lookup"><span data-stu-id="382eb-191">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="382eb-192">Als u wilt toestaan dat meerdere servers referenties delegeren naar _ServerC_, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op een matrix:</span><span class="sxs-lookup"><span data-stu-id="382eb-192">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="382eb-193">Als u de tweede hop tussen domeinen wilt maken, voegt u een volledig gekwalificeerde domein naam (FQDN) toe van de domein controller van het domein waartoe _ServerB_ behoort:</span><span class="sxs-lookup"><span data-stu-id="382eb-193">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="382eb-194">Als u de bevoegdheid voor het delegeren van referenties wilt verwijderen naar ServerC, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op `$null` :</span><span class="sxs-lookup"><span data-stu-id="382eb-194">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="382eb-195">Informatie over op resources gebaseerde Kerberos-beperkte delegering</span><span class="sxs-lookup"><span data-stu-id="382eb-195">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="382eb-196">[Wat is nieuw in Kerberos-verificatie][whats-new]</span><span class="sxs-lookup"><span data-stu-id="382eb-196">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="382eb-197">[Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 1, vereenvoudigt][kcd2012-1]</span><span class="sxs-lookup"><span data-stu-id="382eb-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="382eb-198">[Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 2, vereenvoudigt][kcd2012-2]</span><span class="sxs-lookup"><span data-stu-id="382eb-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="382eb-199">[Meer informatie over Kerberos-beperkte overdracht voor Azure Active Directory-toepassingsproxy-implementaties met geïntegreerde Windows-verificatie][kcdpaper]</span><span class="sxs-lookup"><span data-stu-id="382eb-199">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="382eb-200">[[MS-ADA2] Active Directory schema kenmerken M 2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span><span class="sxs-lookup"><span data-stu-id="382eb-200">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="382eb-201">[[MS-SFU] Kerberos-protocol uitbreidingen: service voor gebruiker en beperkt delegering Protocol 1.3.2 S4U2proxy][MS-SFU]</span><span class="sxs-lookup"><span data-stu-id="382eb-201">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="382eb-202">[Extern beheer zonder beperkte delegering met behulp van PrincipalsAllowedToDelegateToAccount][remote-admin]</span><span class="sxs-lookup"><span data-stu-id="382eb-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="382eb-203">Kerberos-overdracht (onbeperkt)</span><span class="sxs-lookup"><span data-stu-id="382eb-203">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="382eb-204">U kunt ook Kerberos-onbeperkte overdracht gebruiken om de tweede hop te maken.</span><span class="sxs-lookup"><span data-stu-id="382eb-204">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="382eb-205">Net als alle Kerberos-scenario's worden referenties niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="382eb-205">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="382eb-206">Deze methode biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="382eb-206">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="382eb-207">Deze methode biedt geen controle over waar gedelegeerde referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="382eb-207">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="382eb-208">Het is minder veilig dan CredSSP.</span><span class="sxs-lookup"><span data-stu-id="382eb-208">It is less secure than CredSSP.</span></span> <span data-ttu-id="382eb-209">Deze methode mag alleen worden gebruikt voor test scenario's.</span><span class="sxs-lookup"><span data-stu-id="382eb-209">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="382eb-210">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="382eb-210">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="382eb-211">Met JEA kunt u de opdrachten die een beheerder tijdens een Power shell-sessie kan uitvoeren, beperken.</span><span class="sxs-lookup"><span data-stu-id="382eb-211">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="382eb-212">Het kan worden gebruikt om het probleem met de tweede hop op te lossen.</span><span class="sxs-lookup"><span data-stu-id="382eb-212">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="382eb-213">Zie [net genoeg beheer](/powershell/scripting/learn/remoting/jea/overview)voor meer informatie over jea.</span><span class="sxs-lookup"><span data-stu-id="382eb-213">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="382eb-214">**Voordelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-214">**Pros**</span></span>

- <span data-ttu-id="382eb-215">Geen wachtwoord onderhoud wanneer een virtueel account wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="382eb-215">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="382eb-216">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-216">**Cons**</span></span>

- <span data-ttu-id="382eb-217">Vereist WMF 5,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="382eb-217">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="382eb-218">Vereist configuratie op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="382eb-218">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="382eb-219">PSSessionConfiguration met behulp van runas</span><span class="sxs-lookup"><span data-stu-id="382eb-219">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="382eb-220">U kunt een sessie configuratie op _ServerB_ maken en de para meter **RunAsCredential** instellen.</span><span class="sxs-lookup"><span data-stu-id="382eb-220">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="382eb-221">Voor informatie over het gebruik van **PSSessionConfiguration** en **runas** om het probleem met de tweede hop op te lossen, raadpleegt [u een andere oplossing voor externe communicatie met Power shell voor multi-hop][pssessionconfig].</span><span class="sxs-lookup"><span data-stu-id="382eb-221">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="382eb-222">**Voordelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-222">**Pros**</span></span>

- <span data-ttu-id="382eb-223">Werkt met een wille keurige server met WMF 3,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="382eb-223">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="382eb-224">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-224">**Cons**</span></span>

- <span data-ttu-id="382eb-225">Vereist de configuratie van **PSSessionConfiguration** en **runas** op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="382eb-225">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="382eb-226">Vereist wachtwoord onderhoud bij gebruik van een **runas** -account van het domein</span><span class="sxs-lookup"><span data-stu-id="382eb-226">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="382eb-227">Referenties binnen een Invoke-Command-script blok door geven</span><span class="sxs-lookup"><span data-stu-id="382eb-227">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="382eb-228">U kunt referenties door geven binnen de para meter **script Block** van een aanroep naar de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="382eb-228">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="382eb-229">**Voordelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-229">**Pros**</span></span>

- <span data-ttu-id="382eb-230">Vereist geen speciale server configuratie.</span><span class="sxs-lookup"><span data-stu-id="382eb-230">Does not require special server configuration.</span></span>
- <span data-ttu-id="382eb-231">Werkt op elke server waarop WMF 2,0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="382eb-231">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="382eb-232">**Nadelen**</span><span class="sxs-lookup"><span data-stu-id="382eb-232">**Cons**</span></span>

- <span data-ttu-id="382eb-233">Hiervoor is een vreemd-code techniek vereist.</span><span class="sxs-lookup"><span data-stu-id="382eb-233">Requires an awkward code technique.</span></span>
- <span data-ttu-id="382eb-234">Bij het uitvoeren van WMF 2,0 is een andere syntaxis vereist voor het door geven van argumenten aan een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="382eb-234">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="382eb-235">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="382eb-235">Example</span></span>

<span data-ttu-id="382eb-236">In het volgende voor beeld ziet u hoe de referenties worden door gegeven in een script blok voor de **opdracht invoke** :</span><span class="sxs-lookup"><span data-stu-id="382eb-236">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="382eb-237">Zie ook</span><span class="sxs-lookup"><span data-stu-id="382eb-237">See also</span></span>

[<span data-ttu-id="382eb-238">Beveiligingsoverwegingen bij externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="382eb-238">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

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
