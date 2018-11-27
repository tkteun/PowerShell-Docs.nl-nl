---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De tweede hop maken in PowerShell voor externe toegang
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320700"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="00e43-103">De tweede hop maken in PowerShell voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="00e43-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="00e43-104">Het "tweede hop '-probleem verwijst naar een situatie als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="00e43-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="00e43-105">U bent aangemeld bij _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="00e43-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="00e43-106">Van _ServerA_, u verbinding maken met een externe PowerShell-sessie starten _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="00e43-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="00e43-107">Een opdracht die u uitvoert op _ServerB_ via uw externe communicatie van PowerShell sessie probeert te krijgen tot een resource op _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="00e43-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="00e43-108">Toegang tot de resource op _ServerC_ is geweigerd omdat de referenties die u gebruikt voor het maken van de externe communicatie van PowerShell-sessie niet worden doorgegeven van _ServerB_ naar _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="00e43-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="00e43-109">Er zijn verschillende manieren om dit probleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="00e43-109">There are several ways to address this problem.</span></span> <span data-ttu-id="00e43-110">In dit onderwerp bekijken we op verschillende van de meest populaire oplossingen voor het tweede hop-probleem.</span><span class="sxs-lookup"><span data-stu-id="00e43-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="00e43-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="00e43-111">CredSSP</span></span>

<span data-ttu-id="00e43-112">U kunt de [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="00e43-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="00e43-113">CredSSP in de cache opgeslagen referenties op de externe server (_ServerB_), zodat u maximaal referentie diefstal aanvallen met behulp van deze opent.</span><span class="sxs-lookup"><span data-stu-id="00e43-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="00e43-114">Als de externe computer is geknoeid, heeft de aanvaller heeft toegang tot de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="00e43-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="00e43-115">CredSSP is standaard uitgeschakeld in zowel client als server-computers.</span><span class="sxs-lookup"><span data-stu-id="00e43-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="00e43-116">Alleen in de meest vertrouwde omgevingen moet u CredSSP inschakelen.</span><span class="sxs-lookup"><span data-stu-id="00e43-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="00e43-117">Bijvoorbeeld, een domeinbeheerder verbinding te maken met een domeincontroller, omdat de domeincontroller zeer vertrouwd wordt.</span><span class="sxs-lookup"><span data-stu-id="00e43-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="00e43-118">Zie voor meer informatie over problemen met de beveiliging bij het gebruik van CredSSP voor externe communicatie van PowerShell, [per ongeluk Sabotage: Houd er rekening mee van CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="00e43-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="00e43-119">Zie voor meer informatie over referenties diefstal aanvallen [Mitigating Pass-the-Hash (PtH) aanvallen en andere diefstal van referenties](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="00e43-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="00e43-120">Zie voor een voorbeeld van hoe u kunt inschakelen en gebruiken van CredSSP voor externe communicatie van PowerShell, [CredSSP met behulp van de tweede hop-probleem op te lossen](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="00e43-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-121">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-121">Pros</span></span>

- <span data-ttu-id="00e43-122">Dit werkt voor alle servers met Windows Server 2008 of hoger.</span><span class="sxs-lookup"><span data-stu-id="00e43-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-123">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-123">Cons</span></span>

- <span data-ttu-id="00e43-124">Beveiligingsproblemen heeft.</span><span class="sxs-lookup"><span data-stu-id="00e43-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="00e43-125">Configuratie van de client- en -functies vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="00e43-126">Kerberos-overdracht (een)</span><span class="sxs-lookup"><span data-stu-id="00e43-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="00e43-127">U kunt ook een Kerberos-overdracht gebruikt om de tweede hop maken.</span><span class="sxs-lookup"><span data-stu-id="00e43-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="00e43-128">Deze methode biedt echter geen controle over waarop gedelegeerde referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00e43-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="00e43-129">**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="00e43-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="00e43-130">Zie voor meer informatie, [Security Focus: 'Account is vertrouwelijk en kan niet worden overgedragen' analyseren voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="00e43-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-131">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-131">Pros</span></span>

- <span data-ttu-id="00e43-132">Vereist geen speciale codering.</span><span class="sxs-lookup"><span data-stu-id="00e43-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-133">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-133">Cons</span></span>

- <span data-ttu-id="00e43-134">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="00e43-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="00e43-135">Biedt geen controle over waarop referenties worden gebruikt, het maken van een beveiligingsprobleem.</span><span class="sxs-lookup"><span data-stu-id="00e43-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="00e43-136">Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="00e43-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="00e43-137">Verouderde beperkte delegering (geen resource-indeling) kunt u de tweede hop maken.</span><span class="sxs-lookup"><span data-stu-id="00e43-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span>

><span data-ttu-id="00e43-138">**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="00e43-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="00e43-139">Zie voor meer informatie, [Security Focus: 'Account is vertrouwelijk en kan niet worden overgedragen' analyseren voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="00e43-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-140">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-140">Pros</span></span>

- <span data-ttu-id="00e43-141">Vereist geen speciale codering</span><span class="sxs-lookup"><span data-stu-id="00e43-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-142">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-142">Cons</span></span>

- <span data-ttu-id="00e43-143">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="00e43-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="00e43-144">Moet worden geconfigureerd op de Active Directory-object van de externe server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="00e43-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="00e43-145">Beperkt tot één domein.</span><span class="sxs-lookup"><span data-stu-id="00e43-145">Limited to one domain.</span></span> <span data-ttu-id="00e43-146">Kan niet meerdere domeinen of forests.</span><span class="sxs-lookup"><span data-stu-id="00e43-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="00e43-147">Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="00e43-148">Bronnen gebaseerde beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="00e43-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="00e43-149">Met behulp van de resource op basis van Kerberos-beperkte overdracht (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het object van de server waar de resources zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="00e43-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="00e43-150">In de tweede hop-scenario die hierboven worden beschreven, configureert u _ServerC_ om op te geven van waar het accepteert gedelegeerde referenties.</span><span class="sxs-lookup"><span data-stu-id="00e43-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="00e43-151">**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="00e43-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="00e43-152">Zie voor meer informatie, [Security Focus: 'Account is vertrouwelijk en kan niet worden overgedragen' analyseren voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="00e43-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-153">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-153">Pros</span></span>

- <span data-ttu-id="00e43-154">Referenties worden niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="00e43-154">Credentials are not stored.</span></span>
- <span data-ttu-id="00e43-155">Betrekkelijk eenvoudig te configureren met behulp van PowerShell-cmdlets--er zijn geen speciale codering vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="00e43-156">Er zijn geen speciale domeintoegang is vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-156">No special domain access is required.</span></span>
- <span data-ttu-id="00e43-157">Werk met domeinen en forests.</span><span class="sxs-lookup"><span data-stu-id="00e43-157">Works across domains and forests.</span></span>
- <span data-ttu-id="00e43-158">PowerShell-code.</span><span class="sxs-lookup"><span data-stu-id="00e43-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-159">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-159">Cons</span></span>

- <span data-ttu-id="00e43-160">WindowsServer 2012 of hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="00e43-161">Biedt geen ondersteuning voor de tweede hop voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="00e43-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="00e43-162">Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="00e43-163">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="00e43-163">Example</span></span>

<span data-ttu-id="00e43-164">We bekijken een voorbeeld waarmee resources worden geconfigureerd op basis van beperkte delegering van PowerShell _ServerC_ waarmee gedelegeerde referenties van een _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="00e43-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="00e43-165">In dit voorbeeld wordt ervan uitgegaan dat alle servers worden uitgevoerd met WindowsServer 2012 of hoger, en of er ten minste één Windows Server 2012-domeincontroller die een van de servers elk domein behoren.</span><span class="sxs-lookup"><span data-stu-id="00e43-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="00e43-166">Voordat u beperkte delegering configureren kunt, moet u toevoegen de `RSAT-AD-PowerShell` functie als de Active Directory PowerShell-module wilt installeren, en vervolgens importeren die module in uw sessie:</span><span class="sxs-lookup"><span data-stu-id="00e43-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="00e43-167">Verschillende beschikbare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** parameter:</span><span class="sxs-lookup"><span data-stu-id="00e43-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="00e43-168">De **PrincipalsAllowedToDelegateToAccount** parameter stelt het Active Directory-object-kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**, die een toegangsbeheerlijst (ACL) bevat die Hiermee geeft u welke accounts hebben een machtiging voor het overdragen van referenties voor het gekoppelde account (in ons voorbeeld is dit het computeraccount voor _Server_).</span><span class="sxs-lookup"><span data-stu-id="00e43-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="00e43-169">Nu gaan we de variabelen die we gebruiken om weer te geven van de servers instellen:</span><span class="sxs-lookup"><span data-stu-id="00e43-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="00e43-170">WinRM (en dus PowerShell voor externe toegang) wordt uitgevoerd als het computeraccount standaard.</span><span class="sxs-lookup"><span data-stu-id="00e43-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="00e43-171">U kunt dit zien door te kijken de **%{StartName/** eigenschap van de `winrm` service:</span><span class="sxs-lookup"><span data-stu-id="00e43-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="00e43-172">Voor _ServerC_ om toe te staan van de delegatie van een PowerShell-sessie voor externe toegang op _ServerB_, er wordt nu toegang verleend door in te stellen de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ voor het computerobject van _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="00e43-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="00e43-173">De Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches geweigerd toegangspogingen (negatieve cache) gedurende 15 minuten.</span><span class="sxs-lookup"><span data-stu-id="00e43-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="00e43-174">Als _ServerB_ eerder heeft geprobeerd toegang te _ServerC_, moet u de cache wissen op _ServerB_ door het aanroepen van de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="00e43-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="00e43-175">U kunt ook de computer opnieuw opstarten of wacht ten minste 15 minuten om de cache te wissen.</span><span class="sxs-lookup"><span data-stu-id="00e43-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="00e43-176">Na de cache wissen, kunt u met succes-code uitvoeren _ServerA_ via _ServerB_ naar _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="00e43-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="00e43-177">In dit voorbeeld wordt de `$using` variabele wordt gebruikt om de `$ServerC` zichtbaar voor variabele _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="00e43-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="00e43-178">Voor meer informatie over de `$using` variabele, Zie [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="00e43-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="00e43-179">Om toe te staan van meerdere servers om te delegeren referenties _ServerC_, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ naar een matrix:</span><span class="sxs-lookup"><span data-stu-id="00e43-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="00e43-180">Als u maken van de tweede hop in meerdere domeinen wilt, volledig gekwalificeerde domeinnaam (FQDN) van de domeincontroller van het domein aan toevoegen die _ServerB_ behoort:</span><span class="sxs-lookup"><span data-stu-id="00e43-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="00e43-181">Als u wilt verwijderen van de mogelijkheid om te delegeren referenties ServerC, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ naar `$null`:</span><span class="sxs-lookup"><span data-stu-id="00e43-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="00e43-182">Meer informatie over bronnen gebaseerde beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="00e43-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="00e43-183">Wat is er nieuw in Kerberos-verificatie</span><span class="sxs-lookup"><span data-stu-id="00e43-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="00e43-184">Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 1</span><span class="sxs-lookup"><span data-stu-id="00e43-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="00e43-185">Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 2</span><span class="sxs-lookup"><span data-stu-id="00e43-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="00e43-186">Informatie over Kerberos-beperkte overdracht voor Azure Active Directory Application Proxy-implementaties met geïntegreerde Windows-verificatie</span><span class="sxs-lookup"><span data-stu-id="00e43-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="00e43-187">[[MS-ADA2]: Active Directory-Schema kenmerken M2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="00e43-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="00e43-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and beperkte delegering Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="00e43-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="00e43-189">Resource op basis van Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="00e43-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="00e43-190">Extern beheer zonder beperkte delegering met PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="00e43-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="00e43-191">Met RunAs-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="00e43-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="00e43-192">U kunt een sessieconfiguratie maken op _ServerB_ en stel de **RunAsCredential** parameter.</span><span class="sxs-lookup"><span data-stu-id="00e43-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="00e43-193">Zie voor meer informatie over het gebruik van PSSessionConfiguration en uitvoeren als de tweede hop-probleem op te lossen [andere oplossing voor externe communicatie van PowerShell Multihop](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="00e43-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-194">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-194">Pros</span></span>

- <span data-ttu-id="00e43-195">Als u werkt met een server met WMF 3.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="00e43-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-196">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-196">Cons</span></span>

- <span data-ttu-id="00e43-197">Configuratie van vereist **PSSessionConfiguration** en **RunAs** op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="00e43-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="00e43-198">Wachtwoord onderhoud moet worden uitgevoerd bij het gebruik van een domein **RunAs** account</span><span class="sxs-lookup"><span data-stu-id="00e43-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="00e43-199">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="00e43-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="00e43-200">JEA kunt u beperken welke opdrachten die een beheerder kan worden uitgevoerd tijdens een PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="00e43-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="00e43-201">Het kan worden gebruikt om de tweede hop-probleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="00e43-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="00e43-202">Zie voor meer informatie over JEA [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="00e43-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-203">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-203">Pros</span></span>

- <span data-ttu-id="00e43-204">Er is geen wachtwoord onderhoud bij het gebruik van een virtueel account.</span><span class="sxs-lookup"><span data-stu-id="00e43-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-205">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-205">Cons</span></span>

- <span data-ttu-id="00e43-206">WMF 5.0 of hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="00e43-207">Moet worden geconfigureerd op elke tussenliggende server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="00e43-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="00e43-208">Doorgeven van referenties in een scriptblok Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="00e43-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="00e43-209">U kunt doorgeven van referenties in de **ScriptBlock** parameter van een aanroep naar de [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00e43-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="00e43-210">Voordelen</span><span class="sxs-lookup"><span data-stu-id="00e43-210">Pros</span></span>

- <span data-ttu-id="00e43-211">Geen vereist speciale configuratie.</span><span class="sxs-lookup"><span data-stu-id="00e43-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="00e43-212">Werkt op elke server met WMF 2.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="00e43-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="00e43-213">Nadelen</span><span class="sxs-lookup"><span data-stu-id="00e43-213">Cons</span></span>

- <span data-ttu-id="00e43-214">Een techniek onhandige code vereist.</span><span class="sxs-lookup"><span data-stu-id="00e43-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="00e43-215">Als met WMF 2.0, moet andere syntaxis voor het doorgeven van argumenten met een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="00e43-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="00e43-216">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="00e43-216">Example</span></span>

<span data-ttu-id="00e43-217">Het volgende voorbeeld laat zien hoe doorgeven van referenties in een **Invoke-Command** scriptblok:</span><span class="sxs-lookup"><span data-stu-id="00e43-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="00e43-218">Zie ook</span><span class="sxs-lookup"><span data-stu-id="00e43-218">See also</span></span>

[<span data-ttu-id="00e43-219">Beveiligingsoverwegingen bij externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="00e43-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)